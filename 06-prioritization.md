# 6 · Prioritization 🚦

> **The question this answers:** How does the system decide what's P1 vs P2 vs P3 — and how do I make that trustworthy?

[← Grouping](05-grouping.md) · [🏠 Overview](../README.md) · [Next: Reply Suggestions →](07-reply-suggestions.md)

---

## 🚦 The Three Levels

```mermaid
flowchart LR
    P1["🔴 P1 · URGENT<br/>Act today<br/>blocking others"]
    P2["🟡 P2 · IMPORTANT<br/>This week<br/>needs a reply"]
    P3["🟢 P3 · LOW<br/>FYI only<br/>no action"]

    style P1 fill:#FCEBEB,stroke:#E24B4A
    style P2 fill:#FAEEDA,stroke:#BA7517
    style P3 fill:#EAF3DE,stroke:#639922
```

---

## ⚖️ The Scoring Model

Priority isn't one thing — it's **several signals combined into a score**.

```mermaid
flowchart TD
    A["👤 Who sent it<br/>weight: 30%"] --> S["🎯 Priority<br/>Score"]
    B["⏰ Deadline mentioned<br/>weight: 25%"] --> S
    C["❓ Action required<br/>weight: 20%"] --> S
    D["😟 Tone / escalation<br/>weight: 15%"] --> S
    E["🏷️ Sender's flag<br/>weight: 10%"] --> S
    S --> P{Score}
    P -->|"70-100"| P1["🔴 P1"]
    P -->|"40-69"| P2["🟡 P2"]
    P -->|"0-39"| P3["🟢 P3"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#E6F1FB,stroke:#378ADD
    style C fill:#E1F5EE,stroke:#1D9E75
    style D fill:#E1F5EE,stroke:#1D9E75
    style E fill:#F1EFE8,stroke:#888780
    style S fill:#EEEDFE,stroke:#7F77DD
    style P1 fill:#FCEBEB,stroke:#E24B4A
    style P2 fill:#FAEEDA,stroke:#BA7517
    style P3 fill:#EAF3DE,stroke:#639922
```

---

## 🎛️ The Signals Explained

| Signal | What raises priority | Rule or AI? |
|--------|---------------------|:-----------:|
| 👤 **Sender importance** | Your manager, key client, exec | ⚙️ Rule (VIP list) |
| ⏰ **Deadline language** | "by EOD", "urgent", "today" | 🧠 AI |
| ❓ **Action required** | A direct question to you | 🧠 AI |
| 😟 **Escalation tone** | Frustration, repeated follow-up | 🧠 AI |
| 🏷️ **Importance flag** | Sender marked it high | ⚙️ Rule |
| 👥 **To vs CC** | You're in "To" not "CC" | ⚙️ Rule |
| 🤖 **Automated sender** | noreply@ → lowers priority | ⚙️ Rule |

---

## 🔀 The Decision Flow

```mermaid
flowchart TD
    E["📧 Email"] --> A{Automated<br/>sender?}
    A -->|"Yes"| P3["🟢 P3"]
    A -->|"No"| B{From VIP<br/>list?}
    B -->|"Yes"| C{Action or<br/>deadline?}
    B -->|"No"| D{Direct question<br/>to you?}
    C -->|"Yes"| P1["🔴 P1"]
    C -->|"No"| P2["🟡 P2"]
    D -->|"Yes"| P2
    D -->|"No"| P3

    style E fill:#E6F1FB,stroke:#378ADD
    style A fill:#FAEEDA,stroke:#BA7517
    style B fill:#FAEEDA,stroke:#BA7517
    style C fill:#FAEEDA,stroke:#BA7517
    style D fill:#FAEEDA,stroke:#BA7517
    style P1 fill:#FCEBEB,stroke:#E24B4A
    style P2 fill:#FAEEDA,stroke:#BA7517
    style P3 fill:#EAF3DE,stroke:#639922
```

---

## 👑 The VIP List — Your Most Powerful Lever

```mermaid
flowchart LR
    A["📝 config/vips.yaml"] --> B["manager@company.com<br/>bigclient@client.com<br/>ceo@company.com"]
    B --> C["⬆️ Auto-boost<br/>priority"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#FAEEDA,stroke:#BA7517
    style C fill:#FCEBEB,stroke:#E24B4A
```

A simple config file you maintain by hand. **No AI needed, huge accuracy gain.** Build this early.

---

## 🔁 Making It Learn Over Time

```mermaid
flowchart LR
    A["🚦 System assigns<br/>P1/P2/P3"] --> B["👤 You correct it<br/>'this was actually P1'"]
    B --> C["💾 Store the<br/>correction"]
    C --> D["📈 Feed past<br/>corrections as<br/>examples"]
    D --> A

    style A fill:#EEEDFE,stroke:#7F77DD
    style B fill:#FAECE7,stroke:#D85A30
    style C fill:#E6F1FB,stroke:#378ADD
    style D fill:#EAF3DE,stroke:#639922
```

**This is the killer feature.** Store your corrections, then include a few as examples in the prompt. The system gets personalized without any model training.

---

## ⚠️ Design Principle: Never Auto-Delete

```mermaid
flowchart TD
    A["🚦 Priority assigned"] --> B["✅ SAFE: sort, label,<br/>highlight, summarize"]
    A --> C["❌ RISKY: auto-delete,<br/>auto-archive,<br/>auto-send"]

    style A fill:#EEEDFE,stroke:#7F77DD
    style B fill:#EAF3DE,stroke:#639922
    style C fill:#FCEBEB,stroke:#E24B4A
```

The system will get priority wrong sometimes. **Keep it advisory, keep the human deciding.**

---

## ✅ Takeaways

- Priority = **weighted score** from several signals, not one rule
- Mix **rules** (VIP list, CC vs To, automated senders) with **AI** (deadlines, tone)
- Build the **VIP list early** — biggest accuracy win for least effort
- **Store your corrections** and feed them back as examples
- Keep it **advisory** — never auto-delete or auto-send

---

[← Grouping](05-grouping.md) · [🏠 Overview](../README.md) · [Next: Reply Suggestions →](07-reply-suggestions.md)
