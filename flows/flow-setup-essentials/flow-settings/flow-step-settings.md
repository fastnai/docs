# Flow Step Settings

Each **flow component** in Fastn, such as a Switch, Loop, or Action step, includes a **Settings** panel where you can define behavior, retry logic, and notes for that step.

### ⚙️Settings

Use this section to control how the step executes and interacts with the rest of the flow.

To access these options, click the **Settings icon** in the **top-right corner** of the component. Once opened, you'll see the following fields:

<figure><img src="../../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

### Retry Settings _(optional)_

Allows you to configure the **retry behavior** for this step in case of failure.

* [x] **Make Step Required:** Ensures this step is completed before the flow continues.

> Stops the entire flow immediately if this step encounters an error.

<figure><img src="../../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

### Step Note _(optional)_

Add notes or comments about the purpose or logic of this step. This helps collaborators understand context and reasoning within the flow.

<figure><img src="../../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

> 💡 _Adding clear notes to each step makes debugging and collaboration much easier, especially in complex flows._

---

## Related topics

* [Flow Settings](./) — configure flow-level execution, authentication, and error notifications
* [Logger](../designing-a-flow/logger.md) — add logging to your flow steps for debugging and monitoring
* [Flow Response: Success & Error](../designing-a-flow/flow-response-success-and-error.md) — define what happens when a step succeeds or fails
* [Designing a Flow](../designing-a-flow/) — browse all flow components and learn how to build flows
