# 10 · Build Roadmap 🗺️

> **The question this answers:** In what order do I actually build this, and what does "done" look like at each stage?

[← Knowledge Required](09-knowledge-required.md) · [🏠 Overview](../README.md)

---

## 🚀 The Five Phases

```mermaid
flowchart TD
    P1["📡 PHASE 1 · CONNECT<br/>Fetch emails into Python"] --> P2["📝 PHASE 2 · SUMMARIZE<br/>LLM writes one-line gists"]
    P2 --> P3["🗂️ PHASE 3 · ORGANIZE<br/>Group + assign priority"]
    P3 --> P4["✍️ PHASE 4 · REPLY<br/>Draft suggestions"]
    P4 --> P5["🖥️ PHASE 5 · INTERFACE<br/>Streamlit dashboard"]

    style P1 fill:#FAEEDA,stroke:#BA7517
    style P2 fill:#E6F1FB,stroke:#378ADD
    style P3 fill:#E1F5EE,stroke:#1D9E75
    style P4 fill:#EEEDFE,stroke:#7F77DD
    style P5 fill:#EAF3DE,stroke:#639922
```

---

## 📡 Phase 1 · Connect

```mermaid
flowchart LR
    A["Register app<br/>in Azure"] --> B["Get token<br/>via MSAL"]
    B --> C["Fetch 5 emails"]
    C --> D["✅ Print subjects<br/>in notebook"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#FAEEDA,stroke:#BA7517
    style C fill:#E1F5EE,stroke:#1D9E75
    style D fill:#EAF3DE,stroke:#639922
```

**Done when:** you can print 5 email subjects from your real inbox in a notebook.
**Hardest part:** OAuth setup. Expect this to take the longest.

---

## 📝 Phase 2 · Summarize

```mermaid
flowchart LR
    A["Clean email<br/>text"] --> B["Send to LLM"]
    B --> C["Get JSON<br/>back"]
    C --> D["✅ 20 one-line<br/>summaries"]

    style A fill:#FAEEDA,stroke:#BA7517
    style B fill:#EEEDFE,stroke:#7F77DD
    style C fill:#E6F1FB,stroke:#378ADD
    style D fill:#EAF3DE,stroke:#639922
```

**Done when:** you get a clean list of 20 summaries as structured JSON.

---

## 🗂️ Phase 3 · Organize

```mermaid
flowchart LR
    A["Group by<br/>sender domain"] --> B["Group by topic<br/>via LLM"]
    B --> C["Score priority"]
    C --> D["✅ P1/P2/P3<br/>sorted list"]

    style A fill:#E1F5EE,stroke:#1D9E75
    style B fill:#EEEDFE,stroke:#7F77DD
    style C fill:#FAEEDA,stroke:#BA7517
    style D fill:#EAF3DE,stroke:#639922
```

**Done when:** your inbox comes back sorted into groups with priorities attached.
**Build the VIP list here** — biggest accuracy gain.

---

## ✍️ Phase 4 · Reply

```mermaid
flowchart LR
    A["Detect: needs<br/>reply?"] --> B["Build style<br/>profile"]
    B --> C["Generate 2-3<br/>options"]
    C --> D["✅ Draft replies<br/>you'd actually send"]

    style A fill:#FAEEDA,stroke:#BA7517
    style B fill:#E6F1FB,stroke:#378ADD
    style C fill:#EEEDFE,stroke:#7F77DD
    style D fill:#EAF3DE,stroke:#639922
```

**Done when:** drafts sound like you and need only light editing.

---

## 🖥️ Phase 5 · Interface

```mermaid
flowchart LR
    A["Streamlit<br/>skeleton"] --> B["Email cards"]
    B --> C["Priority<br/>sections"]
    C --> D["✅ Dashboard<br/>you use daily"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#E1F5EE,stroke:#1D9E75
    style C fill:#FCEBEB,stroke:#E24B4A
    style D fill:#EAF3DE,stroke:#639922
```

**Done when:** you open it each morning instead of your inbox.

---

## 🔮 Future Ideas (Beyond Phase 5)

```mermaid
flowchart TD
    F["🔮 Future"] --> A["🧠 Learning loop<br/>corrections improve<br/>priority over time"]
    F --> B["🔍 Embeddings<br/>semantic grouping"]
    F --> C["⏰ Scheduled runs<br/>daily 8am digest"]
    F --> D["📅 Calendar aware<br/>'you're free at 3pm'"]
    F --> E["🎯 Agent mode<br/>multi-step actions"]
    F --> G["📎 Attachment<br/>summarizing"]

    style F fill:#FAECE7,stroke:#D85A30
    style A fill:#EEEDFE,stroke:#7F77DD
    style B fill:#E6F1FB,stroke:#378ADD
    style C fill:#E1F5EE,stroke:#1D9E75
    style D fill:#FAEEDA,stroke:#BA7517
    style E fill:#EEEDFE,stroke:#7F77DD
    style G fill:#EAF3DE,stroke:#639922
```

---

## ⏱️ Realistic Timeline

| Phase | Effort | Calendar time (part-time) |
|:-----:|--------|---------------------------|
| 1 · Connect | 🔴 Hardest | 1–2 weeks |
| 2 · Summarize | 🟢 Easy | 2–3 days |
| 3 · Organize | 🟡 Medium | 1 week |
| 4 · Reply | 🟡 Medium | 1 week |
| 5 · Interface | 🟡 Medium | 1 week |

**Total: roughly 4–6 weeks part-time** to a working daily-use tool.

---

## 🎯 The One Rule

```mermaid
flowchart LR
    A["✅ Finish each phase<br/>end-to-end"] --> B["Working thing<br/>at every step"]
    C["❌ Build everything<br/>then test"] --> D["Nothing works<br/>for weeks"]

    style A fill:#EAF3DE,stroke:#639922
    style B fill:#EAF3DE,stroke:#639922
    style C fill:#FCEBEB,stroke:#E24B4A
    style D fill:#FCEBEB,stroke:#E24B4A
```

**Ship each phase before starting the next.** A working Phase 2 beats a half-built Phase 5.

---

## ✅ Takeaways

- Five phases: **Connect → Summarize → Organize → Reply → Interface**
- **Phase 1 is the hardest** — OAuth eats the most time
- **4–6 weeks part-time** to daily-use quality
- **Finish each phase end-to-end** before moving on
- Everything after Phase 5 is optional evolution

---

[← Knowledge Required](09-knowledge-required.md) · [🏠 Overview](../README.md)
