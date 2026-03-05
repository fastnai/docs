---
description: >-
  Set up a Configuration Flow to power user-configurable settings in your
  widget, including static and dynamic dropdowns.
---

# Configuration flows

A Configuration Flow defines the fields and input controls that appear when a user clicks **Configure** on your widget. It translates your flow logic into a form-based UI — dropdowns, text fields, and pickers — that end users interact with directly.

## When do you need a Configuration Flow?

Use this decision to determine whether your widget requires one:

* **Your widget needs user-configurable settings** (dropdowns, file pickers, text inputs) → You need a Configuration Flow.
* **Your flow is pure API or webhook with no widget UI** → You do not need a Configuration Flow.

If a user needs to select a Slack channel, pick a Google Cloud Storage bucket, or enter a custom value through the widget, a Configuration Flow is what makes that possible.

## How it works

A Configuration Flow sits between the widget UI and your data sources. Three components work together:

```
Widget UI  ←  powered by  →  Configuration Flow  ←  gets data from  →  Selection Flow
```

| Component | Role |
|-----------|------|
| **Widget UI** | Renders the configuration form that end users see and interact with |
| **Configuration Flow** | Defines the fields, labels, dropdowns, and validation rules for that form |
| **Selection Flow** | Fetches live data from external connectors (Slack channels, GCS buckets, HubSpot contacts) to populate dynamic dropdowns |

Static dropdowns do not require a Selection Flow — you define the options directly in the Configuration Flow. Dynamic dropdowns call a Selection Flow at runtime to fetch current data.

## 1. Create the Configuration Flow

1. Go to the **Widgets** section in Fastn.
2. Click the arrow next to the **Add Widget** button (top-right corner).
3. Select **Add Configuration Flow**.

<!-- TODO: Screenshot showing the Add Widget dropdown with "Add Configuration Flow" highlighted -->
<figure><img src="../../.gitbook/assets/TODO-config-flow-add-widget-dropdown.png" alt="Add Widget dropdown with Add Configuration Flow option"><figcaption></figcaption></figure>

4. Enter a name for your Configuration Flow and click **Build**.

<!-- TODO: Screenshot showing the flow naming dialog -->
<figure><img src="../../.gitbook/assets/TODO-config-flow-name-dialog.png" alt="Configuration Flow naming dialog"><figcaption></figcaption></figure>

This opens the flow builder where you define the fields your widget exposes to users.

## 2. Add a Data Mapper

The Data Mapper step defines the variables and parameters that become configurable fields in the widget.

1. In the flow builder, click **+** to add a step.
2. Open the **Transformation** tab in the component picker.
3. Select **Data Mapper**.

<!-- TODO: Screenshot showing the component picker with Data Mapper selected under Transformation tab -->
<figure><img src="../../.gitbook/assets/TODO-config-flow-add-data-mapper.png" alt="Component picker with Data Mapper selected"><figcaption></figcaption></figure>

Each variable you add to the Data Mapper becomes a field in the widget's configuration form.

## 3. Configure fields

For each variable in the Data Mapper, click the three-dot menu and select **Options** to configure how the field appears and behaves.

<!-- TODO: Screenshot showing the three-dot menu with Options highlighted -->
<figure><img src="../../.gitbook/assets/TODO-config-flow-field-options-menu.png" alt="Data Mapper variable options menu"><figcaption></figcaption></figure>

### General settings

| Setting | Description |
|---------|-------------|
| **Label** | The display name shown to users in the widget UI |
| **Disable this field** | Prevents user edits (read-only) |
| **Mark as new ID field** | Assigns a unique identifier for the configuration |
| **Hide this field in configuration pop-up** | Keeps the field hidden from the user |
| **Hide based on config field** | Controls visibility based on another field's value |

<!-- TODO: Screenshot showing the General section of field options -->
<figure><img src="../../.gitbook/assets/TODO-config-flow-general-settings.png" alt="General settings panel for a configuration field"><figcaption></figcaption></figure>

### Selections

The **Selections** section determines how users provide values for this field. You can choose from four selection types:

* **Static Selection** — Fixed options you define manually
* **Dynamic Selection** — Live data fetched from a Selection Flow
* **Custom Selection** — Advanced selectors like file pickers
* **Mapping Selection** — Maps fields between source and destination flows

## 4. Set up a static dropdown

Use a Static Selection when the options are fixed and do not change (for example, a list of environments: `Production`, `Staging`, `Development`).

1. In the field's **Options** panel, go to the **Selections** section.
2. Select **Static Selection** as the selection type.
3. Add each option with a **Label** (what the user sees) and a **Value** (what the flow receives).

<!-- TODO: Screenshot showing static selection configuration with label/value pairs -->
<figure><img src="../../.gitbook/assets/TODO-config-flow-static-selection.png" alt="Static Selection configuration with label and value fields"><figcaption></figcaption></figure>

{% hint style="info" %}
For detailed configuration of static options, see [Setting up a Configuration Flow with Static Selection Options](../../resources/library/tutorials/understanding-flow-types/how-to-set-up-a-configuration-flow-in-fastn/setting-up-a-configuration-flow-with-static-selection-options.md).
{% endhint %}

## 5. Set up a dynamic dropdown using a Selection Flow

Use a Dynamic Selection when the dropdown options need to reflect live data from an external service (for example, a list of Slack channels or GCS buckets).

**Prerequisites:** You need a deployed Selection Flow that returns the data for your dropdown. If you do not have one, see [How to Set Up a Selection Flow](../../resources/library/tutorials/understanding-flow-types/how-to-set-up-a-selection-flow.md).

1. In the field's **Options** panel, go to the **Selections** section.
2. Select **Dynamic Selection** as the selection type.
3. Under **Selection Flow**, choose your deployed Selection Flow from the list (it appears under **Workspace Selection Flows** or **Community Selection Flows**).
4. Configure any additional options such as pagination or result limits.

<!-- TODO: Screenshot showing dynamic selection configuration with a Selection Flow selected -->
<figure><img src="../../.gitbook/assets/TODO-config-flow-dynamic-selection.png" alt="Dynamic Selection configuration with Selection Flow dropdown"><figcaption></figcaption></figure>

{% hint style="info" %}
For detailed configuration of dynamic options, see [Setting up a Configuration Flow with Dynamic Selection Options](../../resources/library/tutorials/understanding-flow-types/how-to-set-up-a-configuration-flow-in-fastn/setting-up-a-configuration-flow-with-dynamic-selection-options.md).
{% endhint %}

## 6. Link the Configuration Flow in Settings

> **This is the most commonly missed step.** Without it, your widget shows no configuration options.

After building your Configuration Flow, you must link it to your project in the platform settings. The flow does not automatically appear in the widget.

1. Go to **Settings** in the left sidebar.
2. Select the **Configurations** tab (alongside API Keys, Users, Secrets, Environments, Models, Tenants, and Preferences).
3. Link your Configuration Flow to the appropriate widget or connector.

<!-- TODO: Screenshot showing Settings → Configurations tab with the Configuration Flow linking interface -->
<figure><img src="../../.gitbook/assets/TODO-config-flow-settings-configurations.png" alt="Settings page with Configurations tab showing flow linking"><figcaption></figcaption></figure>

{% hint style="warning" %}
If you skip this step, the widget renders without any configuration options. This is the most frequent cause of "my config is not showing up" issues.
{% endhint %}

4. Deploy or redeploy your widget to apply the changes.

## Common issues

| Problem | Cause | Fix |
|---------|-------|-----|
| Dropdown is empty | Selection Flow is not deployed, or it returns data in an incorrect format | Deploy the Selection Flow and verify it returns a valid list by running a test inside the flow builder |
| No configuration options in widget | Configuration Flow is not linked in **Settings → Configurations** | Go to **Settings → Configurations** and link the Configuration Flow to your widget |
| Changes not showing in widget | The widget was not redeployed after changes | Redeploy the widget after making changes to the Configuration Flow or Selection Flow |
