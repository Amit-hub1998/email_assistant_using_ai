# 📬 AI Email Assistant

> A Python-based assistant that connects to your **Outlook / Gmail** inbox, **summarizes** your emails, **groups** them, assigns **priority**, and **suggests replies** — all powered by an LLM.

---

## 🎯 What It Does

```mermaid
flowchart LR
    A["📥 Inbox<br/>20 emails"] --> B["🔌 Connect<br/>& fetch"]
    B --> C["📝 Summarize<br/>each email"]
    C --> D["🗂️ Group<br/>by sender, topic"]
    D --> E["🚦 Prioritize<br/>P1 · P2 · P3"]
    E --> F["✍️ Suggest<br/>replies"]
    F --> G["🖥️ Show to user"]

    style A fill:#FAECE7,stroke:#D85A30
    style B fill:#FAEEDA,stroke:#BA7517
    style C fill:#E6F1FB,stroke:#378ADD
    style D fill:#E6F1FB,stroke:#378ADD
    style E fill:#EEEDFE,stroke:#7F77DD
    style F fill:#EEEDFE,stroke:#7F77DD
    style G fill:#EAF3DE,stroke:#639922
```

---

## 📚 Documentation Map

| # | Doc | What it covers |
|:-:|-----|----------------|
| 1 | [Architecture](01-architecture.md) | The big picture — where everything runs |
| 2 | [Where to Run It](docs/02-where-to-run-it.md) | Jupyter vs VS Code vs server — decided |
| 3 | [Connecting to Outlook](docs/03-connecting-to-outlook.md) | Auth, Graph API, getting emails into Python |
| 4 | [Fetch & Summarize](docs/04-fetch-and-summarize.md) | Reading the inbox, building summaries |
| 5 | [Grouping Emails](docs/05-grouping.md) | How emails get clustered |
| 6 | [Prioritization](docs/06-prioritization.md) | How P1/P2/P3 gets assigned |
| 7 | [Reply Suggestions](docs/07-reply-suggestions.md) | Generating draft replies |
| 8 | [Interface Options](docs/08-interface.md) | CLI, notebook, or GUI? |
| 9 | [Knowledge Required](docs/09-knowledge-required.md) | Skills roadmap to build this |
| 10 | [Build Roadmap](docs/10-build-roadmap.md) | Phase-by-phase plan |

---

## 🏗️ System at a Glance

```mermaid
flowchart TD
    subgraph Cloud["☁️ Microsoft / Google Cloud"]
        MB["📧 Mailbox"]
        API["🔌 Graph API"]
    end
    subgraph Local["💻 Your Machine"]
        PY["🐍 Python App"]
        LLM["🧠 LLM Client"]
        UI["🖥️ Interface"]
    end
    subgraph AI["🤖 AI Provider"]
        MODEL["Claude / GPT"]
    end

    MB --> API
    API -->|"OAuth token"| PY
    PY --> LLM
    LLM --> MODEL
    MODEL --> LLM
    LLM --> PY
    PY --> UI

    style Cloud fill:#E6F1FB,stroke:#378ADD
    style Local fill:#EAF3DE,stroke:#639922
    style AI fill:#EEEDFE,stroke:#7F77DD
```

---

## 🧰 Tech Stack (High Level)

| Layer | Choice | Why |
|-------|--------|-----|
| 🐍 Language | Python 3.10+ | Best AI/LLM ecosystem |
| 📧 Mail access | Microsoft Graph API | Official, modern, works with Outlook 365 |
| 🔐 Auth | OAuth 2.0 (MSAL library) | Secure, no password storage |
| 🧠 AI | Claude / OpenAI API | Summaries, grouping, replies |
| 🖥️ Interface | Streamlit (recommended) | Fastest path to a real GUI |
| 💾 Storage | SQLite | Simple local cache |

---

## 🚦 Project Status

```mermaid
flowchart LR
    P1["Phase 1<br/>Connect & fetch"] --> P2["Phase 2<br/>Summarize"]
    P2 --> P3["Phase 3<br/>Group & prioritize"]
    P3 --> P4["Phase 4<br/>Reply suggestions"]
    P4 --> P5["Phase 5<br/>GUI"]

    style P1 fill:#FAEEDA,stroke:#BA7517
    style P2 fill:#F1EFE8,stroke:#888780
    style P3 fill:#F1EFE8,stroke:#888780
    style P4 fill:#F1EFE8,stroke:#888780
    style P5 fill:#F1EFE8,stroke:#888780
```

*Start here → [Architecture](docs/01-architecture.md)*
