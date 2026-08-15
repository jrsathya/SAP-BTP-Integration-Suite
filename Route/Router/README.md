# 🚦 Router in SAP CPI

## 🌱 Basics
- **Definition**: The Router is a flow step in SAP Cloud Platform Integration (CPI) used to control message processing paths based on conditions.
- **Purpose**: It allows you to split the integration flow into multiple branches depending on the content of the incoming message.
- **Analogy**: Think of it like a traffic signal — it directs messages to the correct lane based on rules.

---

## ⚙️ How It Works
- The Router evaluates **XPath expressions** or **header/property values**.
- Each branch has a **condition**. If the condition is true, the message flows through that branch.
- If no condition matches, the message goes through the **default branch**.

---

## 📄 Example: Simple Router
### Source XML
```xml
<Order>
   <OrderID>1001</OrderID>
   <Type>Domestic</Type>
</Order>
```

### Router Conditions
- **Condition 1**: `/Order/Type = 'Domestic'`
- **Condition 2**: `/Order/Type = 'International'`

### Flow
- Domestic orders → Domestic processing branch
- International orders → International processing branch
- Others → Default branch

---

## 🔍 Advanced Usage
### 1. **Multiple Conditions**
- You can define multiple branches with complex XPath conditions.
- Example: `/Order/Amount > 1000 and /Order/Type = 'International'`

### 2. **Header/Property Based Routing**
- Instead of payload, you can route based on message headers or properties.
- Example: `header.CorrelationID = 'Payroll'`

### 3. **Dynamic Routing**
- Combine Router with **Content Modifier** or **Groovy Script** to set dynamic properties.
- Example: Use Groovy to extract a field, store it in a property, and route based on that property.

### 4. **Error Handling**
- Router can be used to separate error flows.
- Example: If `/Order/Status = 'Error'`, route to an error-handling branch.

---

## 🛠️ Real-World Scenario
**Payroll Integration Example**  
- Incoming payroll file contains employee type.
- Router conditions:
  - `/Employee/Type = 'Permanent'` → Send to SAP HCM system
  - `/Employee/Type = 'Contract'` → Send to Vendor system
  - Default → Log for manual review

---

## 🚀 Best Practices
- Keep conditions **simple and readable**.
- Always define a **default branch** to avoid message loss.
- Use **properties** for reusable routing logic.
- For complex logic, prefer **Groovy scripts** to avoid long XPath expressions.

---

## 📌 Summary
The Router in SAP CPI is a powerful step that:
- Directs messages based on payload, headers, or properties.
- Supports both simple and advanced conditional logic.
- Enables clean separation of business scenarios in integration flows.
