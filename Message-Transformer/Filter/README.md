# Filter

## Overview

The Filter step is used to control the message flow based on a condition.
If the condition evaluates to **true**, the message continues to the next step.
If the condition evaluates to **false**, the message processing stops.

---

## Use Cases

- Filter records based on business rules
- Process only valid messages
- Skip unwanted payloads
- Validate message content

---

## Example Scenario

Process only purchase orders where:

Amount > 1000

Messages with Amount <= 1000 are discarded.

---

## Configuration

Expression Type:
XPath

Expression:

/Order/Amount > 1000

---

## Input Payload

```xml
<Order>
    <Amount>1500</Amount>
</Order>
```

---

## Output

Message is processed because the condition is TRUE.

---

## Interview Questions

**Q. What happens if the Filter condition is false?**

The message processing stops and no further steps are executed.

---

## Best Practices

- Keep expressions simple.
- Validate XML before using XPath.
- Use Properties or Headers when appropriate.
