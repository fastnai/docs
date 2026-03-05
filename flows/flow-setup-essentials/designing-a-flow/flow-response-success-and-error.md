# Flow Response: Success & Error

Control what gets returned when your flow ends. Customize success or error messages based on HTTP response codes.

<figure><img src="https://docs.fastn.ai/~gitbook/image?url=https%3A%2F%2F1255842839-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F3iSr2Tx8FvvuoLPncziH%252Fuploads%252FDAduJicFuosyr81g6L5w%252Fimage.png%3Falt%3Dmedia%26token%3D71f42458-ebf4-4c2f-8cae-82f88ffad067&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=cb51acfb&#x26;sv=2" alt=""><figcaption></figcaption></figure>

**Example Success Definition**

```
Str Status = "success"  
Str Message = "Order processed"  
Int OrderId = 12345
```

**Example Error Definition**

```
Str Status = "error"  
Str ErrorMessage = "Invalid customer email"
```

---

## Related topics

* [Data Mapping in Flows](data-mapping-in-flows.md#flow-response-success-and-error) — map values from previous steps into your flow response
* [Switch](switch.md) — route to different success or error responses based on conditions
* [Logger](logger.md) — log response details for debugging and monitoring
* [Flow Settings](../flow-settings/) — configure error notifications and custom authentication for your flows
* [How to Customize Success and Error Messages UI in Flows](../../../resources/library/tutorials/flow-customization-and-operations/how-to-customize-success-and-error-messages-ui-in-flows.md) — tutorial on customizing response appearance
