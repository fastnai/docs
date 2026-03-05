---
description: >-
  Add a step to log messages or data objects. Useful for debugging or tracking
  flow activity.
---

# Logger

Use the **Logger** component to record messages, variable values, or object data at any point in your flow.

> It helps you monitor progress, validate logic, and troubleshoot issues by providing real-time insights into flow execution.

<figure><img src="../../../.gitbook/assets/image (660).png" alt=""><figcaption></figcaption></figure>

### **How does it help?**

* Monitor flow execution and debug easily
* Log key events, data points, or outcomes
* Improve visibility and traceability during automation runs

### **Where to view logs?**

All your flow logs are available in the **Logs** section, accessible from the left navigation panel inside your Fastn workspace. You can also view aggregated flow execution metrics on the [Analytics and Monitoring Dashboard](../../../customer-facing-integrations/embedded-integrations/workspace-management/analytics-and-monitoring-dashboard.md).

<figure><img src="../../../.gitbook/assets/image (659).png" alt=""><figcaption></figcaption></figure>

This section displays a list of all your flows including the request and response logs (including start and end points).

* Any **custom Logger entries** you've added as part of your flow steps would be reflected here as well.

<figure><img src="../../../.gitbook/assets/Screenshot 2025-10-31 at 22.45.27.png" alt=""><figcaption></figcaption></figure>

### **Use Case**

Suppose you are processing files inside a **Loop over Templates** step, and each iteration checks a file's processing status. You may want to log the count of:

* Skipped files
* Successfully processed files
* Failed files

#### Steps

* Add a **Logger** step **after** your loop.
* In the **Message** field, enter a summary string such as:

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

> When your flow runs, this message will appear as a **separate log entry** in the **Logs section** of Fastn under that specific flow.

This lets you easily track loop outcomes and data processing metrics without searching through the entire flow execution trace:

<figure><img src="../../../.gitbook/assets/Screenshot 2025-10-31 at 22.45.56.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Use multiple Logger steps in key parts of your flow (e.g., before loops, after variable changes, or after conditional branches) to get detailed, structured insights during execution.
{% endhint %}

---

## Related topics

* [Data Mapping in Flows](data-mapping-in-flows.md#logger) — map values from previous steps into log messages
* [Flow Response: Success & Error](flow-response-success-and-error.md) — structure your final flow output alongside logging
* [Loop](loop.md) — log iteration results and track loop progress
* [Variables](variables.md) — log variable values at different points in the flow
* [Flow Settings](../flow-settings/) — configure error notifications to complement logging
* [Analytics and Monitoring Dashboard](../../../customer-facing-integrations/embedded-integrations/workspace-management/analytics-and-monitoring-dashboard.md) — view flow execution metrics and logs
