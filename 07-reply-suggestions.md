# 7 · Reply Suggestions ✍️

> **The question this answers:** How does the assistant draft replies that actually sound like me?

[← Prioritization](06-prioritization.md) · [🏠 Overview](../README.md) · [Next: Interface →](08-interface.md)

---

## 🎯 Not Every Email Needs a Reply

```mermaid
flowchart TD
    E["📧 Email"] --> Q{Needs a<br/>reply?}
    Q -->|"No · FYI, automated"| A["⏭️ Skip"]
    Q -->|"Yes"| B["✍️ Generate<br/>draft options"]

    style E fill:#E6F1FB,stroke:#378ADD
    style Q fill:#FAEEDA,stroke:#BA7517
    style A fill:#F1EFE8,stroke:#888780
    style B fill:#EAF3DE,stroke:#639922
```

**First decision is binary.** Only generate replies where they're actually needed — saves tokens and noise.

---

## 🎭 Give Options, Not One Answer

```mermaid
flowchart LR
    A["📧 Email"] --> B["🧠 LLM"]
    B --> C["✅ Option 1<br/>Accept / agree"]
    B --> D["⏸️ Option 2<br/>Need more time"]
    B --> E["❓ Option 3<br/>Ask a question"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#EEEDFE,stroke:#7F77DD
    style C fill:#EAF3DE,stroke:#639922
    style D fill:#FAEEDA,stroke:#BA7517
    style E fill:#E1F5EE,stroke:#1D9E75
```

Different **intents**, not just different tones. You pick the direction, then edit.

---

## 🗣️ Making It Sound Like You

```mermaid
flowchart TD
    A["📤 Your past<br/>sent emails"] --> B["🔍 Extract style<br/>greeting, sign-off,<br/>formality, length"]
    B --> C["📋 Style profile"]
    C --> D["🧠 Include in<br/>every reply prompt"]
    D --> E["✍️ Drafts that<br/>sound like you"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#E1F5EE,stroke:#1D9E75
    style C fill:#FAEEDA,stroke:#BA7517
    style D fill:#EEEDFE,stroke:#7F77DD
    style E fill:#EAF3DE,stroke:#639922
```

**The trick:** pull ~10 of your sent emails, have the LLM describe your style once, save that description, and paste it into every reply prompt. Cheap and surprisingly effective.

---

## 🎚️ Tone Should Match the Group

```mermaid
flowchart LR
    A["🏢 Internal"] --> A1["Casual, brief"]
    B["👔 Client"] --> B1["Formal, careful"]
    C["🏬 Vendor"] --> C1["Neutral, direct"]
    D["👑 Executive"] --> D1["Concise, no fluff"]

    style A fill:#E1F5EE,stroke:#1D9E75
    style A1 fill:#E1F5EE,stroke:#1D9E75
    style B fill:#FAECE7,stroke:#D85A30
    style B1 fill:#FAECE7,stroke:#D85A30
    style C fill:#FAEEDA,stroke:#BA7517
    style C1 fill:#FAEEDA,stroke:#BA7517
    style D fill:#EEEDFE,stroke:#7F77DD
    style D1 fill:#EEEDFE,stroke:#7F77DD
```

Your grouping work from Doc 5 **feeds directly into this** — the group tells the LLM which tone to use.

---

## 🛡️ The Human-in-the-Loop Rule

```mermaid
flowchart TD
    A["✍️ Draft generated"] --> B["👤 You review"]
    B --> C{Good?}
    C -->|"Yes"| D["📤 You click send"]
    C -->|"Edit"| E["✏️ You adjust"]
    C -->|"No"| F["🔄 Regenerate"]
    E --> D
    F --> A

    style A fill:#EEEDFE,stroke:#7F77DD
    style B fill:#FAECE7,stroke:#D85A30
    style C fill:#FAEEDA,stroke:#BA7517
    style D fill:#EAF3DE,stroke:#639922
    style E fill:#E6F1FB,stroke:#378ADD
    style F fill:#E6F1FB,stroke:#378ADD
```

**Never auto-send.** The assistant drafts; you approve. This is non-negotiable for anything touching real people.

---

## ⚠️ What to Watch For

| Risk | Mitigation |
|------|-----------|
| 🤥 **Invented facts** | Never let it state details not in the thread |
| 📅 **Fake commitments** | Don't let it promise dates you didn't approve |
| 🔒 **Leaking context** | Don't include unrelated emails in the prompt |
| 🎭 **Wrong tone** | Match tone to the sender group |

---

## ✅ Takeaways

- **Decide first** whether a reply is even needed
- Offer **2–3 options with different intents**, not one draft
- Build a **style profile** from your sent mail — sounds like you, cheaply
- **Tone follows the group** from your grouping logic
- **Always human-in-the-loop.** Draft, never auto-send

---

[← Prioritization](06-prioritization.md) · [🏠 Overview](../README.md) · [Next: Interface →](08-interface.md)
