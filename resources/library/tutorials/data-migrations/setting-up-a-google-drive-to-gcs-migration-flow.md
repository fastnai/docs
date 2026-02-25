---
description: >-
  Migrate files from Google Drive to Google Cloud Storage for each tenant,
  preserving folder structures, handling Google file formats, and avoiding
  duplicate uploads based on file update timestamps.
---

# Setting Up a Google Drive to GCS Migration Flow

## **1. Start the Flow**

You can start the flow by selecting **New API Request** as the trigger.

![](<../../../../.gitbook/assets/image (179).png>)<br>

### Initiate Your Flow Variables

When the flow starts, the following important variables are initialized:

<figure><img src="../../../../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You also define MIME handling for Docs, Sheets, Slides, and Drawings so that Google-native files can be exported in the correct format during migration.
{% endhint %}

***

## **2. Configure Drive and GCS Settings**

### Map Get Configs

The next step maps values from your [**DriveConfigFlow** ](setting-up-a-google-drive-to-gcs-migration-widget.md#configuration-flow-drive_to_gcs)so the flow has all required tenant and bucket details.<br>

<figure><img src="../../../../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

### Create Bucket for Tenant

Once these values are ready, you can use the Google Cloud Storage connector to create a **bucket for the tenant** if it doesn’t already exist.

<figure><img src="../../../../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>

***

## **3. Set the File Path Rules**

You will then hit a **Switch** step that determines how the `filePath` variable is set:

<figure><img src="../../../../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

* If `baseFilePath` is provided → set `filePath` = `{{var.baseFilePath}}`

<figure><img src="../../../../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>

* If `separateFoldersForUsers` is `true` → set `filePath` per tenant/user

<figure><img src="../../../../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure>

* Else → set `filePath` = `"Google Drive"`

<figure><img src="../../../../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure>

From here, you move into the **Loop Over Input** step.

***

## **4. Loop Over Input Items**

<figure><img src="../../../../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

For each item in your incoming list of file IDs:

* Use the Google Drive connector with **getFile**
  * `File ID` = `{{steps.loopOverInput.loopOverItem.value}}`
  * `param.fields` = `id,name,mimeType,modifiedTime`

<figure><img src="../../../../.gitbook/assets/image (189).png" alt=""><figcaption></figcaption></figure>

* Initialize `fileObject` from `loopOverItem`

<figure><img src="../../../../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>

* Append this file object to the `files` array using the advanced action **insertItem**.

{% hint style="info" %}
You can click the three-dots next to your variable to setup or edit the advanced action selected.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>

***

## **5. Loop Over Files**

After the Loop Over Input ends, the next step will be a loop  that runs until all files are processed.

**i. Initialize Loop Counters and Variables**

<figure><img src="../../../../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

* **Data Mapper:** `fileLength = arrayLength(var.files)` ; total files in the queue.

<figure><img src="../../../../.gitbook/assets/image (162).png" alt=""><figcaption></figcaption></figure>

#### Switch Statement

* If no files remain, exit the loop.
*   Else, set:

    * `currentFile = {{var.files[0]}}` , the file you’ll process now.

    <figure><img src="../../../../.gitbook/assets/image (163).png" alt=""><figcaption></figcaption></figure>

    * Remove the first item from `var.files` using `removeItem`.

<figure><img src="../../../../.gitbook/assets/image (164).png" alt=""><figcaption></figcaption></figure>

**ii. Switch Statement to Check If Current File is a Folder**

<figure><img src="../../../../.gitbook/assets/image (165).png" alt=""><figcaption></figcaption></figure>

*   If `currentFile.mimeType` indicates a folder:

    *   Call **Google Drive Connector** with action to **getFilesFromFolder** with:

        * `param.q = '{{var.currentFile.file.id}}' in parents`
        * `param.fields = files(id,name,mimeType,modifiedTime)`

        <figure><img src="../../../../.gitbook/assets/image (166).png" alt=""><figcaption></figcaption></figure>
    * Append each returned file to `var.files` so they’re picked up in the same loop.

    <figure><img src="../../../../.gitbook/assets/image (167).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (168).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (169).png" alt=""><figcaption></figcaption></figure>

**Non-Folder Files**

* Build a **state key** for this file:

<figure><img src="../../../../.gitbook/assets/image (171).png" alt=""><figcaption></figcaption></figure>

*   **Read State** for `stateKey` to check if the file is already processed or unchanged.

    <figure><img src="../../../../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>

#### iii. Switch Step to Check if Files are Updated

Next Step is a switch statement that checks if files are updated, and ends the flow if there is no update.

<figure><img src="../../../../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure>

If the file is updated,

* Run **gettingMimeType** JS step → detect MIME type and extension.

```
function handler(params) {
  const mimeTypes = params?.data.var.mimeTypes;
  const fileMimeTypes = params?.data.var.currentFile.file.metadata?.mimeType;

  for (let i = 0; i < mimeTypes.length; i++) {
    if (mimeTypes[i].googleMimeType === fileMimeTypes) {
      return {
        mimeType: mimeTypes[i].exportableMimeTypes,
        extension: mimeTypes[i].exportablExtension
      };
    }
  }
```

* Run **preparingParams** JS step → prepare download/export URLs.

```
function handler(params) {
  const fileId = params?.data.var.currentFile.file.value;
  let fileNamePrefix = '';
  if (params?.data.input.overrideFiles === false) {
    fileNamePrefix = Date.now() + '_';
  }

  return {
    googleUrl: 'https://www.googleapis.com/drive/v3/files/' + fileId + '/export?mimeType=' + params?.data.steps.gettingMimeType.output.mimeType,
    nonGoogleUrl: 'https://www.googleapis.com/drive/v3/files/' + fileId + '?alt=media',
    fileNamePrefix
  };
}
```

* Get access token from **Fastn Connector** using the action **getConnectorToken**.

<figure><img src="../../../../.gitbook/assets/image (174).png" alt=""><figcaption></figcaption></figure>

**iv. Decide How to Download (Switch Step)**

<figure><img src="../../../../.gitbook/assets/image (499).png" alt=""><figcaption></figcaption></figure>

*   **If Google-native file (Docs, Sheets, Slides, Drawings):**

    <figure><img src="../../../../.gitbook/assets/image (500).png" alt=""><figcaption></figcaption></figure>
*   **Else (non-Google file):**

    <figure><img src="../../../../.gitbook/assets/image (501).png" alt=""><figcaption></figcaption></figure>

**v. Download from Drive**

*   For both types of files, the variables that are initialized will connect to the flow component **Download file** where you can download these files.

    <figure><img src="../../../../.gitbook/assets/image (502).png" alt=""><figcaption></figcaption></figure>

**vi. Upload to Google Cloud Storage**

* In the next step, you will use the **Google Cloud Storage** connector with the action **uploadFileToGCS** with your target bucket and `fileName`.

<figure><img src="../../../../.gitbook/assets/image (503).png" alt=""><figcaption></figcaption></figure>

**vii. Update File State**

* In the next step, you will use the State component to overwrite the State for StateKey depending on the updates.

<figure><img src="../../../../.gitbook/assets/image (505).png" alt=""><figcaption></figcaption></figure>

* Loop picks up next `currentFile` and continues until `var.files` is empty.

***

## **6. Finish the Migration**

The loop continues until all files are processed.\
When complete, the main flow returns a success message confirming the migration.

<figure><img src="../../../../.gitbook/assets/image (506).png" alt=""><figcaption></figcaption></figure>
