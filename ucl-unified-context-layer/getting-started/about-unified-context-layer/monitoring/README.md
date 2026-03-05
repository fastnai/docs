---
description: >-
  The Insights page helps you track everything happening across your tenants,
  connectors, and actions. It is divided into three main parts: Overview, Tool
  Usage, and Logs.
---

# Monitoring

To access the monitoring tools, simply go to the **Insights** section in the top navigation bar of your Dashboard.

<figure><img src="../../../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

### Overview Dashboard

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-11 at 11.40.40 PM (1).png" alt=""><figcaption></figcaption></figure>



The dashboard represents each action triggered by a connector (e.g., sending a message, syncing data) and monitors them across key metrics:

* **Active Tenants (%)** – total tenants connected and their active percentage.
* **Active Connectors** – number of connectors currently in use.
* **Tenant Request Success Rate** – percentage of successful requests per tenant.
* **Monthly Usage** – number of actions performed this month.
* **Weekly Usage** – number of actions performed this week.
* **Today's Usage** – number of actions performed today.
* **Connection Success Rate** – percentage of successful connector connections.
* **Average API Latency** – average time an API takes to respond.
* **Average Workload Latency** – average time a workload (background process) takes to complete.
* **Total Data Transfer** – total volume of data transferred across tenants.
* **Tenant Usage Summary** – per-tenant details including names, connections, errors, and total data transferred.
* **Most Used Connectors** – list of the top connectors in your workspace.
* **Connection Error Rate** – percentage of connection errors across all tenants.

{% hint style="info" %}
Workspace-specific data is not displayed here.
{% endhint %}

### Tool Usage

* A **graph** shows tool usage trends for the current month (date-wise).
* **App Breakdown** section lists:
  * Tool (the app name)
  * Tool calls
  * Tool used
  * Response usage
* Use the **filter** at the top to switch between current month or current week views.

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-11 at 11.40.54 PM.png" alt=""><figcaption></figcaption></figure>



### Logs

The logging system provides detailed visibility into every action performed.

* **Filter by status** to quickly narrow down logs.
* View details for each action, including:
  * Connector name
  * Action performed
  * Status
  * Duration
  * Request time

{% hint style="info" %}
Expand a log entry to view the **full request details**.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-09-11 at 11.31.45 PM.png" alt=""><figcaption></figcaption></figure>

By clicking the **→** button, you can access detailed insights for individual logs, including:

* Unique log IDs
* Timestamps
* Detailed request parameters and responses

<figure><img src="../../../../.gitbook/assets/image (443).png" alt=""><figcaption></figcaption></figure>

### **Why Monitoring Matters**

* **Privacy & Ownership** – Each tenant's monitoring data is strictly isolated, with full control over their data access and retention policies.
* **Faster Issue Resolution** – Easily trace failures to a specific connector, tool, or tenant.
* **Operational Confidence** – Know which parts of your system are underperforming or underutilized.
* **Security & Compliance** – Every request is tenant-scoped and logged, making audits and access reviews simple.
* **Scalability** – As you grow, dashboards help ensure consistent quality of service across all users.

> UCL doesn't just route and execute, it gives you full observability to manage and optimize your integration layer with confidence.

---

## Related topics

* [UCL security and compliance](ucl-security-and-compliance.md) — enterprise-grade security controls, audit trails, and compliance readiness
* [About Unified Context Layer](../) — understand UCL's architecture, multitenancy, and core capabilities
* [Logger](../../../../flows/flow-setup-essentials/designing-a-flow/logger.md) — add logging steps inside Fastn flows for detailed request tracing
* [Analytics and monitoring dashboard](../../../../customer-facing-integrations/embedded-integrations/workspace-management/analytics-and-monitoring-dashboard.md) — track usage and performance across your embedded integrations
