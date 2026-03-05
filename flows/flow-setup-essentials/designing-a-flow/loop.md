# Loop

Repeat actions in a controlled way using the **Loop** flow component:

<figure><img src="https://docs.fastn.ai/~gitbook/image?url=https%3A%2F%2F1255842839-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F3iSr2Tx8FvvuoLPncziH%252Fuploads%252FHp6qLW5glBYyiRkSSOoJ%252Fimage.png%3Falt%3Dmedia%26token%3D8a0aaea8-cbdc-44f4-97cb-74ec3d4b808a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=909a8e72&#x26;sv=2" alt=""><figcaption></figcaption></figure>

> You can select the Loop Type and the Data you want to loop over, mapping it from previous flow steps.

* **Loop N times**: Run a block a fixed number of times.
* **Loop over data**: Iterate through each item in a list.
* **While loop**: Keep looping as long as a condition is true.

Use **End Loop** to mark where the loop finishes.

In the example shown, the **Loop Type** is set to _Loop over data,_ and the **Loop Data** field is mapped from a previous step:

```
{{steps.sendMessage.output.message.blocks}}
```

This means the loop will go through each `block` inside the `message` output from the `sendMessage` step, allowing you to process every block one by one.

<figure><img src="https://docs.fastn.ai/~gitbook/image?url=https%3A%2F%2F1255842839-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F3iSr2Tx8FvvuoLPncziH%252Fuploads%252FoOe0bAvfenYGPkENLvTj%252Fimage.png%3Falt%3Dmedia%26token%3Dd5e58cec-56b6-463e-9952-e659c4317f8d&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=2ac136ef&#x26;sv=2" alt=""><figcaption></figcaption></figure>

---

## Related topics

* [Data Mapping in Flows](data-mapping-in-flows.md#loop) — learn how to map data into and out of loop iterations
* [Variables](variables.md) — store counters or flags to control loop behavior
* [Switch](switch.md) — add conditional logic inside or after a loop
* [Logger](logger.md) — log loop iteration results for debugging
* [How to Set Up Pagination in Your Flow](../../../resources/library/tutorials/flow-customization-and-operations/how-to-set-up-pagination-in-your-flow.md) — tutorial on looping through paginated API results
* [Filter](flow-transformation/filter.md) — filter loop output to keep only matching records
