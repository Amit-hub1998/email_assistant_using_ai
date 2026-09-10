# 5 · Grouping Emails 🗂️

> **The question this answers:** How do 20 scattered emails get organized into meaningful groups?

[← Fetch & Summarize](04-fetch-and-summarize.md) · [🏠 Overview](../README.md) · [Next: Prioritization →](06-prioritization.md)

---

## 🎯 The Goal

```mermaid
flowchart LR
    A["📥 20 scattered<br/>emails"] --> B["🗂️ 5 clear<br/>groups"]
    B --> C["🧠 You process<br/>by theme, not<br/>one-by-one"]

    style A fill:#FBEAF0,stroke:#D4537E
    style B fill:#E6F1FB,stroke:#378ADD
    style C fill:#EAF3DE,stroke:#639922
```

---

## 🔀 Four Ways to Group

```mermaid
flowchart TD
    G["🗂️ Grouping<br/>strategies"] --> A["👤 By sender<br/>who sent it"]
    G --> B["🏢 By source/dept<br/>which team or system"]
    G --> C["📌 By topic<br/>what it's about"]
    G --> D["🧵 By thread<br/>same conversation"]

    style G fill:#EEEDFE,stroke:#7F77DD
    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#E1F5EE,stroke:#1D9E75
    style C fill:#FAEEDA,stroke:#BA7517
    style D fill:#EAF3DE,stroke:#639922
```

---

## ⚖️ Rules vs AI — Use Both

```mermaid
flowchart TD
    E["📧 Email"] --> R{Can a simple<br/>rule handle it?}
    R -->|"Yes"| A["⚙️ RULE-BASED<br/>domain, thread ID,<br/>keyword match<br/>✅ free & instant"]
    R -->|"No"| B["🧠 AI-BASED<br/>semantic topic<br/>✅ smart<br/>❌ costs tokens"]
    A --> C["🗂️ Final groups"]
    B --> C

    style E fill:#E6F1FB,stroke:#378ADD
    style R fill:#FAEEDA,stroke:#BA7517
    style A fill:#EAF3DE,stroke:#639922
    style B fill:#EEEDFE,stroke:#7F77DD
    style C fill:#E1F5EE,stroke:#1D9E75
```

**Golden rule:** Do the cheap deterministic grouping first (sender domain, thread ID), then use the LLM only for what rules can't do (semantic topics).

---

## 🏢 Grouping by Source — The Practical One

```mermaid
flowchart TD
    A["📧 Inbox"] --> B["@yourcompany.com<br/>→ Internal"]
    A --> C["@clientname.com<br/>→ Client"]
    A --> D["noreply@ / alerts@<br/>→ Automated"]
    A --> E["@vendor.com<br/>→ Vendor"]
    A --> F["Unknown domain<br/>→ External / New"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#E1F5EE,stroke:#1D9E75
    style C fill:#FAECE7,stroke:#D85A30
    style D fill:#F1EFE8,stroke:#888780
    style E fill:#FAEEDA,stroke:#BA7517
    style F fill:#FBEAF0,stroke:#D4537E
```

This is **pure Python, no AI needed** — just parse the sender domain. Fast, free, reliable.

---

## 🧠 Topic Grouping with AI

For "what is this actually about," you need the LLM.

```mermaid
flowchart LR
    A["20 summaries"] --> B["🧠 LLM:<br/>'Group these into<br/>3-6 topics'"]
    B --> C["📊 Returns:<br/>Project Alpha (5)<br/>Budget (4)<br/>Hiring (3)<br/>Misc (8)"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#EEEDFE,stroke:#7F77DD
    style C fill:#EAF3DE,stroke:#639922
```

**Tip:** Feed it the **summaries**, not the full emails. Cheaper and the topics come out cleaner.

---

## 🎨 What the Output Looks Like

```mermaid
flowchart TD
    I["📥 Inbox · 20 emails"] --> G1["🏢 Internal · 8"]
    I --> G2["👔 Clients · 5"]
    I --> G3["🤖 Automated · 4"]
    I --> G4["🏬 Vendors · 3"]

    G1 --> S1["Project Alpha · 5<br/>Budget review · 3"]
    G2 --> S2["Escalation · 2<br/>Status update · 3"]

    style I fill:#E6F1FB,stroke:#378ADD
    style G1 fill:#E1F5EE,stroke:#1D9E75
    style G2 fill:#FAECE7,stroke:#D85A30
    style G3 fill:#F1EFE8,stroke:#888780
    style G4 fill:#FAEEDA,stroke:#BA7517
    style S1 fill:#EAF3DE,stroke:#639922
    style S2 fill:#EAF3DE,stroke:#639922
```

**Two levels:** source group first, topic sub-group inside. This is what makes 20 emails feel manageable.

---

## ✅ Takeaways

- Group by **sender, source, topic, or thread** — often several at once
- **Rules first** (free, instant), **AI second** (for meaning)
- Sender-domain grouping is pure Python — start there
- Feed **summaries** to the LLM for topic grouping, not full text
- Two-level output (source → topic) is the most useful shape

---

[← Fetch & Summarize](04-fetch-and-summarize.md) · [🏠 Overview](../README.md) · [Next: Prioritization →](06-prioritization.md)
