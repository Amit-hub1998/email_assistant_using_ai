# 1 · Architecture 🏗️

> **The question this answers:** What are the moving parts, and how do they talk to each other?

[🏠 Overview](../README.md) · [Next: Where to Run It →](02-where-to-run-it.md)

---

## 🧩 The Four Pieces

Every email assistant has exactly four parts. Understand these and the rest is detail.

```mermaid
flowchart TD
    A["1️⃣ MAIL SOURCE<br/>Outlook / Gmail<br/>where emails live"] --> B["2️⃣ CONNECTOR<br/>Graph API + OAuth<br/>gets emails into Python"]
    B --> C["3️⃣ BRAIN<br/>Python + LLM<br/>summarize, group, prioritize"]
    C --> D["4️⃣ INTERFACE<br/>CLI / Notebook / GUI<br/>shows you the result"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#FAEEDA,stroke:#BA7517
    style C fill:#EEEDFE,stroke:#7F77DD
    style D fill:#EAF3DE,stroke:#639922
```

---

## 🔄 The Full Data Flow

```mermaid
sequenceDiagram
    participant U as 👤 You
    participant UI as 🖥️ Interface
    participant PY as 🐍 Python App
    participant MS as 📧 Graph API
    participant AI as 🧠 LLM

    U->>UI: "Summarize my inbox"
    UI->>PY: Trigger run
    PY->>MS: Request emails (with token)
    MS->>PY: Return 20 emails (JSON)
    PY->>PY: Clean & prepare text
    PY->>AI: Send emails + instructions
    AI->>PY: Summaries + groups + priority
    PY->>UI: Structured results
    UI->>U: Display dashboard
```

---

## 🗺️ Where Each Piece Physically Lives

```mermaid
flowchart LR
    subgraph MSC["☁️ Microsoft Cloud"]
        M1["Your mailbox"]
        M2["Graph API endpoint"]
    end
    subgraph YOU["💻 Your Laptop"]
        Y1["Python script"]
        Y2["Local cache (SQLite)"]
        Y3["Streamlit UI"]
    end
    subgraph AIC["☁️ AI Provider"]
        A1["Claude / GPT API"]
    end

    M1 --- M2
    M2 <-->|"HTTPS"| Y1
    Y1 <--> Y2
    Y1 <-->|"HTTPS"| A1
    Y1 --> Y3

    style MSC fill:#E6F1FB,stroke:#378ADD
    style YOU fill:#EAF3DE,stroke:#639922
    style AIC fill:#EEEDFE,stroke:#7F77DD
```

**Key insight:** Your Python app runs **locally on your machine**. It reaches *out* to two clouds (mail + AI). Nothing needs to be hosted anywhere to start.

---

## 📦 Suggested Project Layout

```
email-assistant/
├── src/
│   ├── connector.py      # Talks to Graph API
│   ├── summarizer.py     # LLM calls for summaries
│   ├── grouper.py        # Clustering logic
│   ├── prioritizer.py    # P1/P2/P3 rules
│   ├── replier.py        # Draft reply generation
│   └── app.py            # Streamlit UI
├── config/
│   └── settings.py       # API keys, thresholds
├── data/
│   └── cache.db          # Local SQLite
└── notebooks/
    └── explore.ipynb     # For experimenting
```

---

## ✅ Takeaways

- Four parts: **Source → Connector → Brain → Interface**
- Python runs **locally**, reaching out to mail cloud + AI cloud
- Keep each part in **its own module** so you can evolve them independently
- Nothing needs hosting until you want it always-on

---

[🏠 Overview](../README.md) · [Next: Where to Run It →](02-where-to-run-it.md)
