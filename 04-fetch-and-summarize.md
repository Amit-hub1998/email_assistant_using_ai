# 4 · Fetch & Summarize 📝

> **The question this answers:** Once I have the emails, how do I turn 20 messages into useful summaries?

[← Connecting to Outlook](03-connecting-to-outlook.md) · [🏠 Overview](../README.md) · [Next: Grouping →](05-grouping.md)

---

## 🔄 The Pipeline

```mermaid
flowchart LR
    A["📥 Fetch<br/>raw emails"] --> B["🧹 Clean<br/>strip HTML,<br/>signatures"]
    B --> C["✂️ Trim<br/>fit context<br/>window"]
    C --> D["🧠 LLM<br/>summarize"]
    D --> E["📋 Structured<br/>output"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#FAEEDA,stroke:#BA7517
    style C fill:#FAEEDA,stroke:#BA7517
    style D fill:#EEEDFE,stroke:#7F77DD
    style E fill:#EAF3DE,stroke:#639922
```

---

## 🧹 Why Cleaning Matters

Raw emails are messy. Sending them straight to an LLM wastes context and confuses it.

```mermaid
flowchart TD
    A["📧 Raw email"] --> B["❌ HTML tags"]
    A --> C["❌ Email signatures"]
    A --> D["❌ Legal disclaimers"]
    A --> E["❌ Quoted reply chains"]
    A --> F["✅ The actual message"]
    F --> G["🧠 Send only this<br/>to the LLM"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#FBEAF0,stroke:#D4537E
    style C fill:#FBEAF0,stroke:#D4537E
    style D fill:#FBEAF0,stroke:#D4537E
    style E fill:#FBEAF0,stroke:#D4537E
    style F fill:#EAF3DE,stroke:#639922
    style G fill:#EEEDFE,stroke:#7F77DD
```

---

## 🎯 Two Ways to Summarize

```mermaid
flowchart TD
    Q{How many emails<br/>per LLM call?}
    Q -->|"One at a time"| A["🎯 Per-email<br/>✅ Accurate<br/>❌ 20 API calls"]
    Q -->|"All at once"| B["📦 Batched<br/>✅ 1 API call<br/>❌ May lose detail"]
    A --> C["💡 Best: batch in<br/>groups of 5"]
    B --> C

    style Q fill:#FAEEDA,stroke:#BA7517
    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#E1F5EE,stroke:#1D9E75
    style C fill:#EAF3DE,stroke:#639922
```

---

## 📋 Ask for Structured Output

Don't ask the LLM for prose — ask for **JSON**. Then Python can use it directly.

```mermaid
flowchart LR
    A["📧 Email text"] --> B["🧠 LLM<br/>+ instructions:<br/>'return JSON'"]
    B --> C["{ summary,<br/>category,<br/>urgency,<br/>action_needed }"]
    C --> D["🐍 Python reads<br/>it directly"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#EEEDFE,stroke:#7F77DD
    style C fill:#FAEEDA,stroke:#BA7517
    style D fill:#EAF3DE,stroke:#639922
```

### The fields worth extracting

| Field | Why you need it |
|-------|----------------|
| `summary` | One-line gist |
| `sender_type` | Internal / client / vendor / automated |
| `topic` | For grouping later |
| `action_needed` | Does it need a reply? |
| `deadline_mentioned` | Feeds priority |
| `sentiment` | Detect frustration/escalation |

**These fields become the input for grouping and prioritization** — that's why you extract them now.

---

## 💰 Cost & Speed Awareness

```mermaid
flowchart LR
    A["More emails"] --> B["More tokens"]
    B --> C["Higher cost<br/>+ slower"]
    C --> D["💡 Mitigations"]
    D --> E["Use bodyPreview<br/>not full body"]
    D --> F["Cache results<br/>in SQLite"]
    D --> G["Use a smaller<br/>model for simple<br/>steps"]

    style A fill:#E6F1FB,stroke:#378ADD
    style C fill:#FBEAF0,stroke:#D4537E
    style D fill:#FAEEDA,stroke:#BA7517
    style E fill:#EAF3DE,stroke:#639922
    style F fill:#EAF3DE,stroke:#639922
    style G fill:#EAF3DE,stroke:#639922
```

---

## ✅ Takeaways

- **Clean before you send** — strip HTML, signatures, quoted chains
- **Batch in small groups** (~5 emails) to balance cost and accuracy
- **Always request JSON**, never prose — Python needs structure
- Extract the fields that **feed grouping and priority** later
- **Cache** so you never re-summarize the same email twice

---

[← Connecting to Outlook](03-connecting-to-outlook.md) · [🏠 Overview](../README.md) · [Next: Grouping →](05-grouping.md)
