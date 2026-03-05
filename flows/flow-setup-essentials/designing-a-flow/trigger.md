---
description: Initiate a flow whenever a specific event occurs in a connected app
---

# Trigger

It helps you start automated actions based on real-time activities such as new messages, form submissions, or updates in integrated systems.

<figure><img src="../../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

* You can add this component by searching for **Trigger** in your flow. Once added, you'll first need to **select an app** from the available list or search for the required one.&#x20;

<figure><img src="../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

* After selecting the app, connect and authenticate your account to enable access.

<figure><img src="../../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

* After saving, the Trigger will automatically listen for the selected event.

{% hint style="info" %}
Based on the selected app, a list of **Trigger events** will appear.&#x20;
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

> &#x20;In the case of Slack, when a message is posted in the specified channel, the trigger will activate and send a message from Fastn to that channel.

* Next, select the **account ID** associated with the connection, for example, _Fastn_.&#x20;
* In the **Headers** section, add the required key–value pairs for authentication or configuration. Once you've entered all details, click **Save** to finalize this step.

<figure><img src="../../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

* You can choose the event that should start your flow. For example, when integrating with Slack, you can select the **Message Posted** trigger event.

<figure><img src="../../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

* You can test this step by clicking the **Test** button in the top right corner.&#x20;

> The console will display the result, and you'll see the message sent to your selected Slack channel.

<figure><img src="../../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

---

## Related topics

* [Flow Setup Essentials](../) — overview of all five flow trigger types (API Request, App Event, Webhook, Schedule, Chat)
* [Connectors](connectors.md) — connect to external apps and APIs within your flow steps
* [Setting up Connector Authentication](../connecting-apps/setting-up-connector-authentication.md) — configure OAuth, API Key, or Bearer Token for your connected apps
* [Data Mapping in Flows](data-mapping-in-flows.md) — map trigger outputs into downstream flow steps
* [How to Set Up an Activation Flow](../../../resources/library/tutorials/understanding-flow-types/how-to-set-up-an-activation-flow.md) — tutorial on using triggers in activation flows
