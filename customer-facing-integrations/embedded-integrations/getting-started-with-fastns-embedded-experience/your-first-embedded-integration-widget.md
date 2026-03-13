---
description: >-
  Build your first embedded integration widget from scratch, embed it in a
  sample app, and walk through the end-user experience of connecting a Slack
  account.
---

# Your first embedded integration widget

In this tutorial, you will create a Fastn widget that lets your end-users connect their Slack account directly from your application. By the end, you will have:

- A working widget with Slack as the dependency connector
- An Activate action linked to a flow
- The widget deployed to your LIVE environment
- A sample HTML page with the widget embedded via iframe
- A connected Slack account authenticated through the widget

This tutorial takes approximately 15 minutes.

## Prerequisites

Before you start, make sure you have:

- A Fastn account with an active workspace. [Sign up at fastn.ai](https://fastn.ai) if you do not have one.
- A project created in your workspace. Copy your **Project ID** from the URL — it appears after `/project/` in the Fastn dashboard.
- A basic text editor for creating the sample HTML page.

{% hint style="info" %}
This tutorial uses Slack as the example connector. The same process works for Google, GitHub, Jira, Shopify, or any of Fastn's 250+ connectors.
{% endhint %}

## Step 1: Create the widget

1. In the Fastn dashboard, go to the **Widgets** page.
2. Click **Add Widget** in the top-right corner.
3. Select **With a connector**.
4. Search for **Slack** and select it.

Fastn creates a new widget with Slack's details pre-filled, including the name, image, and description.

{% hint style="info" %}
You can pick from Fastn's built-in connectors or connectors from your own workspace.
{% endhint %}

### Verify

The widget editor opens with Slack listed under **Dependency Connectors**. The Slack connector appears as the **Primary** connector.

## Step 2: Configure the dependency connector

The dependency connector defines which third-party service your end-users authenticate with when they interact with the widget.

1. In the widget editor, confirm that **Slack** appears under **Dependency Connectors**.
2. Verify the connector details:
   - **Name**: Slack
   - **Authentication**: OAuth (default)

The default OAuth settings use Fastn's managed Slack credentials. Your end-users authenticate through Slack's standard OAuth consent screen, and Fastn handles token storage and refresh.

{% hint style="info" %}
To use your own Slack app credentials, click **Auth Attributes** on the Slack connector and provide your `clientId`, `clientSecret`, and desired scopes. See [Overriding widget connector auth attributes](previewing-and-integrating-widgets.md#overriding-widget-connector-auth-attributes) for details.
{% endhint %}

## Step 3: Add an Activate action

Actions define what happens when an end-user interacts with the widget. The **Activate** action is the primary entry point — it triggers authentication and runs your activation logic.

1. Under **Actions**, click **Add**.
2. Configure the action:

| Field          | Value                                     |
| -------------- | ----------------------------------------- |
| **Name**       | Activate                                  |
| **Flow**       | Select an activation flow from Templates  |
| **Visibility** | Always                                    |
| **Action**     | Activation                                |

3. To use a pre-built activation flow, go to the **Flows** page, click **Templates**, and import an Activation flow template. Then return to the widget editor and select that flow.

{% hint style="info" %}
The Activation flow runs after the end-user completes Slack OAuth. You can add steps to this flow later, such as posting a welcome message to the user's Slack workspace or registering webhooks.
{% endhint %}

### Verify

The Activate action appears in the **Actions** list with the flow linked and action type set to **Activation**.

## Step 4: Save and deploy to LIVE

1. Click **Update** to save the widget configuration.
2. Click **Deploy to LIVE** at the bottom of the page.

This deploys the widget and all connected flows to your LIVE environment, making them available to end-users.

### Verify

The widget status changes to **Deployed**. You can confirm by going to the **Widgets** page and checking that the Slack widget shows an active deployment indicator.

## Step 5: Preview the widget

Before embedding, preview how the widget looks to end-users.

1. On the **Widgets** page, click the **Integrate** button.
2. Click **Preview**.
3. A new browser tab opens showing the widget in draft mode.

You should see a card with the Slack logo, a description, and an **Activate** button. This is the view your end-users will see.

{% hint style="info" %}
The preview page always shows the **DRAFT** version. To preview the deployed LIVE version, add `?env=LIVE` to the URL query parameters.
{% endhint %}

## Step 6: Get the embed code

1. On the **Widgets** page, click **Integrate**.
2. Select the **Iframe** tab.
3. Choose **HTML** (or **React** if your application uses React).
4. Copy the generated code snippet.

The snippet contains three configuration values you need to update:

```javascript
projectId: "<PROJECT_ID>",  // Your workspace project ID
tenantId: "<TENANT_ID>",    // A unique identifier for the end-user
authToken: "<AUTH_TOKEN>"    // Token for custom authentication (optional)
```

| Parameter   | Description                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------------------ |
| `projectId` | Your workspace Project ID. Find it in the dashboard URL after `/project/`.                                   |
| `tenantId`  | A unique identifier for the end-user in your system (for example, a user ID or customer ID).                 |
| `authToken` | A token for custom authentication. Leave as a placeholder for now — it is only required when custom auth is enabled. |

## Step 7: Embed the widget in a sample page

Create an HTML file to test the embedded widget. Replace `YOUR_PROJECT_ID` with your actual Project ID.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My App - Integrations</title>
  <style>
    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      margin: 0;
      padding: 2rem;
      background-color: #f5f5f5;
    }
    h1 { margin-bottom: 1rem; }
    .widget-container {
      width: 100%;
      max-width: 900px;
      height: 600px;
      border: 1px solid #e0e0e0;
      border-radius: 8px;
      overflow: hidden;
      background: white;
    }
    iframe {
      width: 100%;
      height: 100%;
      border: none;
    }
  </style>
</head>
<body>
  <h1>Integrations</h1>
  <p>Connect your favorite tools to get started.</p>
  <div class="widget-container">
    <iframe
      src="https://app.fastn.ai/connect/YOUR_PROJECT_ID?tenantId=demo-user-1&env=LIVE"
      allow="clipboard-write"
    ></iframe>
  </div>
</body>
</html>
```

Save this file as `integrations.html` and open it in your browser.

{% hint style="info" %}
Replace `YOUR_PROJECT_ID` with your actual Project ID. The `tenantId=demo-user-1` value represents the end-user. In production, replace this with the authenticated user's ID from your system.
{% endhint %}

### Verify

The page displays a heading, a description, and the Fastn widget inside a bordered container. The Slack widget card is visible with an **Activate** button.

## Step 8: Connect a Slack account

This is the end-user experience. Walk through it to see what your users will encounter:

1. Open the sample HTML page in your browser.
2. Click the **Activate** button on the Slack widget card.
3. A Slack OAuth consent screen opens in a popup or new tab.
4. Sign in to a Slack workspace and authorize the requested permissions.
5. After authorization, the popup closes and the widget updates to show the connected state.

Fastn stores the end-user's Slack connection securely under their `tenantId` in its SOC 2 certified vault. Your application code never sees the raw Slack OAuth tokens.

### Verify

The widget card changes from showing **Activate** to showing post-authentication actions (such as **Disconnect** or **Configure**, if you added those actions). In the Fastn dashboard, you can verify the connection under your project's connection logs.

## Step 9: Use the connection in your back end (optional)

With the Slack connection established, you can use the Fastn SDK to execute actions on behalf of the end-user:

```python
from fastn import FastnClient

fastn = FastnClient(
    api_key="your-api-key",
    project_id="your-project-id",
)

# Send a message using the end-user's Slack connection
fastn.slack.send_message(
    tenant_id="demo-user-1",
    channel="general",
    text="Hello from our integration!",
)
```

Fastn automatically resolves the correct Slack connection for the specified `tenant_id` and handles token refresh behind the scenes.

## Summary

In this tutorial, you:

1. Created a widget with Slack as the dependency connector
2. Added an Activate action linked to a flow
3. Deployed the widget to LIVE
4. Embedded the widget in a sample HTML page using an iframe
5. Walked through the end-user OAuth flow to connect a Slack account
6. Saw how to use the connection from your back-end code

## Next steps

- **Add more actions**: Add Deactivate and Configure actions to give end-users control over their connection. See [Building and configuring widgets](building-and-configuring-widgets-in-fastn.md).
- **Customize the widget theme**: Match the widget styling to your application's design system from the **Integrate > Styling** tab.
- **Enable custom authentication**: Validate end-user tokens from your identity provider (Keycloak, Auth0, Supabase) before loading the widget. See [Setting up custom authentication](previewing-and-integrating-widgets.md#setting-up-custom-authentication).
- **Use the headless React package**: Build a fully custom UI with the [`@fastn-ai/react-core`](https://www.npmjs.com/package/@fastn-ai/react-core) package instead of an iframe. See the [example application](https://github.com/fastnai/react-core-client).
- **Add more connectors**: Repeat this process with Google, GitHub, Jira, or any of Fastn's 250+ connectors.
- **Filter widgets per tenant**: Dynamically show or hide widgets based on business logic. See [Filtering widgets](previewing-and-integrating-widgets.md#filtering-widgets).
