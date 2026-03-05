---
description: >-
  Learn how to configure authentication for any Connector inside your Fastn
  Workspace.
---

# Setting up Connector Authentication

Fastn supports multiple authentication types, including **OAuth, Basic Auth, API Key, Bearer Token,** and **Custom Input.**

## **Setting up Connector Authentication**

When [creating a connector](connector-types-and-setup.md#ii.-workspace-connectors) in the Fastn Workspace, you can configure its authentication by enabling 'Activation' to reveal all available authentication types, or you can access and edit these settings later by clicking the three dots at the top-right of your connector.

<figure><img src="../../../.gitbook/assets/image (691).png" alt=""><figcaption></figcaption></figure>

* You will now see all available authentication modes.

{% hint style="info" %}
These options only appear when **Enable Activation** is checked.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (692).png" alt=""><figcaption></figcaption></figure>

### **Setting Up Custom Input Authentication**

Use this when a connector requires a simple API key, secret key, or any custom field.&#x20;

In the **Custom Input** section, you can define fields such as the API key, its description, the input type (password or text), whether it is required, and any expiry-related information.

<figure><img src="../../../.gitbook/assets/image (693).png" alt=""><figcaption></figcaption></figure>

#### **Example Input Configuration**

```
{
  "apiKey": {
    "description": "API Key:",
    "type": "password",
    "required": true
  },
  "expires_in": {
    "type": "number",
    "default": 100000,
    "hidden": true,
    "disabled": true
  }
}
```

> When the user clicks **Connect**, Fastn will display the custom input fields, and if the field type is set to password, the value will remain hidden.

<figure><img src="../../../.gitbook/assets/image (694).png" alt=""><figcaption></figcaption></figure>

### **Setting Up OAuth Authentication**

> Use this when the platform supports an OAuth login screen (e.g., Google, Microsoft, Slack).&#x20;

In the **OAuth** section, you can configure the base URL, client ID, client secret (if required), scope, authorization parameters, required attributes, and the tenant ID.

<figure><img src="../../../.gitbook/assets/image (696).png" alt=""><figcaption></figcaption></figure>

#### **What does this section handle?**

This part manages the login redirect, the consent popup, and retrieving the authorization code.

{% hint style="info" %}
&#x20;It does not generate access tokens.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (697).png" alt=""><figcaption></figcaption></figure>

### **Setting Up OAuth2 \[Authorization & Token Exchange]**

The **OAuth2 Authorization** section is used to exchange the authorization code for an access token, retrieve refresh tokens, and define how tokens should be renewed when they expire:

* **OAuth Grant Type**: Specifies how Fastn should request the access token.
* **Access Token URL**: URL used to fetch the access token.
* **Refresh Token Grant Type**: Defines how expired tokens should be refreshed.

<figure><img src="../../../.gitbook/assets/image (698).png" alt=""><figcaption></figcaption></figure>

### **Example OAuth Configurations**

In the same format, you can configure OAuth authentication for other connectors as well. For instance, a Microsoft connector would use a configuration like this:

#### **Microsoft OAuth**

```json
{
  "baseUrl": "",
  "clientId": "",
  "params": {
    "scope": "Application.ReadWrite.All AppRoleAssignment.ReadWrite.All ExternalUserProfile.ReadWrite.All DelegatedPermissionGrant.ReadWrite.All Directory.ReadWrite.All User.Read.All openid offline_access",
    "response_type": "code",
    "prompt": "consent"
  },
  "requiredAttributes": [],
  "tenantId": "default",
  "response_type": "code",
  "authorization": {
    "oauthGrantType": "authCodeGrantWithGrantType",
    "accessTokenUrl": "",
    "refreshTokenGrantType": "updatingRefreshTokenRequestType",
    "requestBodyType": "form",
    "refresh_expires_in": "7776000"
  }
}

```

---

## Related topics

* [Connector Types & Setup](connector-types-and-setup.md) — learn about the different connector categories available in Fastn
* [Managing & Using Connectors](managing-and-using-connectors.md) — add and use authenticated connectors in your flows
* [Flow Settings](../flow-settings/) — enable custom authentication at the flow level
* [How to Customize Your Authentication Flow](../../../resources/library/tutorials/flow-customization-and-operations/how-to-customize-your-authentication-flow.md) — tutorial on customizing the authentication experience for end users
* [How to Manage Multiple App Connections Together](../../../resources/library/tutorials/flow-customization-and-operations/how-to-manage-multiple-app-connections-together.md) — tutorial on managing grouped connections
