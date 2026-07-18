# Groovy Script

## Overview

Groovy Script is used to implement custom logic when standard SAP CPI components cannot meet the business requirement.

---

## Common Use Cases

- Modify XML
- Modify JSON
- Remove namespaces
- Generate UUID
- Date conversion
- String manipulation
- Logging
- Custom validation

---

## Example Scenario

Remove XML namespaces from the incoming payload.

---

## Sample Code

```groovy
import com.sap.gateway.ip.core.customdev.util.Message

def Message processData(Message message) {
    def body = message.getBody(String)
    body = body.replaceAll('xmlns="[^"]*"', '')
    message.setBody(body)
    return message
}
```

---

## Input

```xml
<Employee xmlns="test">
    <ID>100</ID>
</Employee>
```

---

## Output

```xml
<Employee>
    <ID>100</ID>
</Employee>
```

---

## Interview Questions

**Q. When do you use Groovy instead of a Content Modifier?**

Use Groovy when complex logic cannot be implemented using standard SAP CPI steps.

---

## Best Practices

- Keep scripts reusable.
- Avoid unnecessary processing.
- Handle exceptions properly.
- Add comments for readability
