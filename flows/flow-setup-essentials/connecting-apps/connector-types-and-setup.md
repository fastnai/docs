---
description: >-
  Connectors are used to seamlessly integrate data from various data sources and
  APIs into your created flows.
---

# Connector Types & Setup

## Connectors in Fastn

Connectors in the **Fastn** platform enable you to integrate and interact with external systems such as APIs, databases, or custom logic. They act as bridges that bring external data into your flows or send processed data out.

## Using Connectors

Connectors are components that simplify the process of integrating third-party services. Once added to a flow, they can perform operations like fetching data, transforming it, or saving it to an external system. Each connector includes input and output schemas to ensure data consistency throughout your flow.

## **Types of Connectors**

In **Fastn**, connectors let your flows interact with external apps, APIs, and data sources. They act as bridges between Fastn and the outside world, enabling powerful automations across tools and services.

Fastn supports three main types of connectors:

## **i. Community Connectors**

These are prebuilt, ready-to-use connectors that let you integrate popular apps like **Slack, Google Docs, Notion, Salesforce, HubSpot**, and many more; with **140+ supported apps and counting**.

Community connectors make it easy to connect to tools your team already uses, so you can trigger flows, pull in data, or take actions in those apps without writing any custom code.

### Example: Using a Google Doc and Slack Connector

To create a Google Doc and send it to a specific Slack channel, utilize the **Google Docs Connector** with **Create Doc Endpoint**  to generate your document and then use the **Slack Connector** with **Send Message Endpoint** to send it directly to your selected channel. This process requires no coding, streamlining document sharing within your workflows.

<figure><img src="../../../.gitbook/assets/image (243).png" alt="Flow editor with Google Docs Create Doc connector followed by Slack Send Message connector"><figcaption></figcaption></figure>

## ii. Workspace Connectors

You can add your own custom connector groups with multiple connectors of your choice.

{% hint style="info" %}
You can also use the **Build with AI** button to leverage AI to assist in creating custom connector groups as needed.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (250).png" alt="Workspace Connectors page with Add Connector button and Build with AI option"><figcaption></figcaption></figure>

To add a new connector group, you need to click on the **Add Connector** button in the top right corner and then fill in the following fields:

<figure><img src="../../../.gitbook/assets/image (252).png" alt="Add Connector Group form with fields for name, image URL, description, documentation link, and resource type"><figcaption></figcaption></figure>

1. **Name**: Enter a unique name for the connector group. This field is required.
2. **Image URL**: Provide a URL for an image to visually represent the connector group.
3. **Description**: Enter a brief description to explain the purpose and functionality of the connector group.
4. **Documentation Link**: Add a link to the documentation for further details about the connector.
5. **Resource Type**: Specify if the resource type is **EXTERNAL** or **INTERNAL**.
6. **Enable Activation**: Toggle the option to enable or disable activation for the connector group.

Inside the group that you create, you can add or delete individual connectors.

<figure><img src="../../../.gitbook/assets/image (253).png" alt="List of individual connectors within a workspace connector group"><figcaption><p>List of Connectors in a Connector Group</p></figcaption></figure>

You can export or import these Connectors and download the corresponding **OpenAPI File.**

<figure><img src="../../../.gitbook/assets/image (254).png" alt="Connector options menu showing export, import, and download OpenAPI file actions"><figcaption></figcaption></figure>

## iii. Organization Connectors

These connectors can be defined at the organization level, allowing any member within the organization to access and utilize the connections provided. This allows for streamlined organization and application of connections across various parts of the organization.

<figure><img src="../../../.gitbook/assets/image (242).png" alt="Organization Connectors page showing shared connectors available to all organization members"><figcaption></figcaption></figure>

{% hint style="info" %}
Similar to Workspace connectors, you can define group connectors and then manage different categories of connectors within them.&#x20;
{% endhint %}
