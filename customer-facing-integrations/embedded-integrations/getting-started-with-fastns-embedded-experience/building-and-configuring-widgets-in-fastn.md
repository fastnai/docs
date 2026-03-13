---
description: >-
  Learn how to build and configure interactive widgets in Fastn to connect apps,
  control actions, and deploy them seamlessly for end-users.
---

# Building and Configuring Widgets in Fastn

## **1. Add a New Widget**

* Click on the **Add Widget** button located at the top-right corner.
* Choose whether to publish the widget **with or without a connector**.
* **Search and select** a connector the widget should handle.

{% hint style="info" %}
You can pick from **Fastn’s built-in connectors** or connectors from **your own workspace**.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F3iSr2Tx8FvvuoLPncziH%2Fuploads%2FgeF1ThCniyyMxZUNuVie%2F20250630-2307-58.4172888.mp4?alt=media&token=c36e49e3-26ba-4c72-ad3b-51bca0057494" %}

## **2. Configure Widget Settings**

Inside the widget editor:

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F3iSr2Tx8FvvuoLPncziH%2Fuploads%2FgfmkWZ87XYnIpFO2xgYi%2F20250630-2313-56.1995988.mp4?alt=media&token=49da2a4c-9da5-4ba6-b20a-52c93bb4c8d5" %}

#### **a. Tenant Visibility**

* Toggle **“Enable for specific tenants”** if the widget should only appear for selected tenants.
* Click **Add tenants** to specify which tenants can access it.

#### **b. Widget Availability**

* Use the **Disable** toggle if you want to temporarily hide the widget from users and select your preferred **Data flow Label** for that.

### **Set Dependency Connectors**

If your widget relies on one or more connectors, specify them under **Dependency Connectors**:

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F3iSr2Tx8FvvuoLPncziH%2Fuploads%2F6u0mLUZbSL1kxT0ih67v%2F20250630-2323-22.1880147.mp4?alt=media&token=84bdae6d-ca30-4430-9dd1-50b233b76672" %}

* Add required connectors (e.g., Slack).
* Mark **Primary** connectors if needed.
* Provide connector image and details such as:
  * **Name**: Slack
  * **Image URL**
  * **Description**: Enables real-time communication and automation by integrating with Slack channels and messages.
* For setting up authentication in your connector, utilize the **Auth Attributes** option to select your preferred authentication method. You can customize the details which will be merged with the default OAuth settings to enable users to switch methods. Choose from the following options:

i. OAuth (default)

ii. Custom Input

iii. API Key

iv. Bearer Token

v. Basic Auth



{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F3iSr2Tx8FvvuoLPncziH%2Fuploads%2FIL70y3qUCPU3Tbijx0aQ%2F20250702-0603-24.8695930.mp4?alt=media&token=9da72cea-61fc-42e3-9fbe-58a6fb16dcfe" %}

## **3. Add Actions to the Widget**

Widgets allow you to define flow-based actions that can be triggered through UI interactions.

Click **"Add"** under **Actions** and configure the following:

| Field          | Description                                                        |
| -------------- | ------------------------------------------------------------------ |
| **Name**       | Action name (e.g., `Activate`, `Deactivate`, `Configure`)          |
| **Flow**       | Select the associated Fastn Flow                                   |
| **Visibility** | Set visibility conditions (e.g., Always)                           |
| **Action**     | Define the action type: Activation, Deactivation, or Configuration |

{% hint style="info" %}
In each action item, you can add the built-in **Activate**, **Deactivate**, or **Configure** flows. These allow you to control the state of your connected app, for example, Slack; directly from your widget. Once added, each of these flows will appear as a button in the widget interface, enabling users to trigger them as needed.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F3iSr2Tx8FvvuoLPncziH%2Fuploads%2FnO7QVfP4rukJ064CXmqn%2F20250630-2337-01.4989660.mp4?alt=media&token=53157e8e-a7dd-4e7e-819a-fb2d9fd69df4" %}

You can get the pre-built activate, deactivate and configure flows from the flows section by clicking on **Templates.**

### Activate Flow

This flow is used to activate your connected app (e.g., Slack). Once triggered, it transitions the integration into an active state.

<figure><img src="../../../.gitbook/assets/image (257).png" alt="Activate flow template in the Fastn flow editor for enabling a connected app integration"><figcaption></figcaption></figure>

### Deactivate Flow

This flow deactivates the app, disconnecting or disabling it as defined in your deactivation logic.

<figure><img src="../../../.gitbook/assets/image (256).png" alt="Deactivate flow template in the Fastn flow editor for disabling a connected app integration"><figcaption></figcaption></figure>

### Configure Flow

Use this flow to allow users to configure settings for the connected app. It can open a form or input model based on what you've defined in the configuration flow.

<figure><img src="../../../.gitbook/assets/image (258).png" alt="Configure flow template in the Fastn flow editor for managing connected app settings"><figcaption></figcaption></figure>

## **4. Deploy to Live**

Once all actions and configurations are complete:

* Deploy the widget to your selected environment by clicking on the "Deploy to LIVE" button at the buttom. This will deploy all your connected flows to your live environment to make it available to end-users.
* You can go to **Preview** from **Integrate** section on the **Widgets** page to see how the widget will appear to the end-users.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F3iSr2Tx8FvvuoLPncziH%2Fuploads%2Fut4ot4GOeNA5IZXOnFy4%2F20250702-0554-40.6684873.mp4?alt=media&token=0e89fe33-eca6-4364-b953-9a3c520d5b0d" %}

