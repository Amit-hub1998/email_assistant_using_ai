# 9 · Knowledge Required 🎓

> **The question this answers:** What do I actually need to know to build this — and what can I learn along the way?

[← Interface](08-interface.md) · [🏠 Overview](../README.md) · [Next: Build Roadmap →](10-build-roadmap.md)

---

## 🗺️ The Skill Map

```mermaid
flowchart TD
    ROOT["🎯 Build the<br/>Email Assistant"] --> A["🐍 Python<br/>core"]
    ROOT --> B["🔌 APIs &<br/>Auth"]
    ROOT --> C["🧠 LLM<br/>Engineering"]
    ROOT --> D["🖥️ Interface"]
    ROOT --> E["💾 Data<br/>handling"]

    style ROOT fill:#FAECE7,stroke:#D85A30
    style A fill:#EAF3DE,stroke:#639922
    style B fill:#FAEEDA,stroke:#BA7517
    style C fill:#EEEDFE,stroke:#7F77DD
    style D fill:#E6F1FB,stroke:#378ADD
    style E fill:#E1F5EE,stroke:#1D9E75
```

---

## 📋 Skills Breakdown by Difficulty

| Skill | What for | Difficulty | Must-have? |
|-------|---------|:----------:|:----------:|
| 🐍 **Python basics** | Everything | 🟢 Easy | ✅ Required |
| 📦 **Dicts & JSON** | Handling email data | 🟢 Easy | ✅ Required |
| 🌐 **REST APIs** | Calling Graph API | 🟡 Medium | ✅ Required |
| 🔐 **OAuth 2.0** | Authentication | 🟡 Medium | ✅ Required |
| 🧠 **Prompt engineering** | Summaries, grouping | 🟡 Medium | ✅ Required |
| 📋 **Structured output** | Getting JSON from LLM | 🟡 Medium | ✅ Required |
| 🐼 **Pandas** | Organizing results | 🟢 Easy | ⭐ Helpful |
| 💾 **SQLite** | Caching | 🟢 Easy | ⭐ Helpful |
| 🖥️ **Streamlit** | The GUI | 🟡 Medium | ⏳ Phase 3 |
| 🔍 **Embeddings** | Smarter grouping | 🔴 Hard | ⏳ Optional |
| 🎯 **Agents** | Full autonomy | 🔴 Hard | ⏳ Later |

---

## 🎯 The Critical Path — Learn These First

```mermaid
flowchart LR
    A["1️⃣ Python<br/>+ JSON"] --> B["2️⃣ REST API<br/>calls"]
    B --> C["3️⃣ OAuth<br/>tokens"]
    C --> D["4️⃣ LLM API<br/>calls"]
    D --> E["5️⃣ Structured<br/>prompting"]
    E --> F["✅ You can build<br/>Phases 1-4"]

    style A fill:#EAF3DE,stroke:#639922
    style B fill:#E1F5EE,stroke:#1D9E75
    style C fill:#FAEEDA,stroke:#BA7517
    style D fill:#E6F1FB,stroke:#378ADD
    style E fill:#EEEDFE,stroke:#7F77DD
    style F fill:#FAECE7,stroke:#D85A30
```

**Five skills gets you a working assistant.** Everything else is enhancement.

---

## 🧠 The LLM Concepts That Matter Here

```mermaid
flowchart TD
    A["🧠 LLM knowledge<br/>for this project"] --> B["✍️ Prompt design<br/>clear instructions"]
    A --> C["📋 Structured output<br/>forcing JSON"]
    A --> D["🪟 Context limits<br/>how much fits"]
    A --> E["💰 Token costs<br/>batching wisely"]
    A --> F["🌡️ Temperature<br/>consistency vs creativity"]

    style A fill:#EEEDFE,stroke:#7F77DD
    style B fill:#E6F1FB,stroke:#378ADD
    style C fill:#E6F1FB,stroke:#378ADD
    style D fill:#E1F5EE,stroke:#1D9E75
    style E fill:#FAEEDA,stroke:#BA7517
    style F fill:#EAF3DE,stroke:#639922
```

**Temperature tip:** use **low temperature** for summarizing and prioritizing (you want consistency), **higher** for reply drafts (you want variety in the options).

---

## 🚫 What You Do NOT Need

```mermaid
flowchart TD
    A["❌ Not required"] --> B["Machine learning<br/>theory"]
    A --> C["Training your<br/>own models"]
    A --> D["Deep learning<br/>math"]
    A --> E["Frontend<br/>JS/React"]
    A --> F["Kubernetes /<br/>DevOps"]

    style A fill:#FBEAF0,stroke:#D4537E
    style B fill:#F1EFE8,stroke:#888780
    style C fill:#F1EFE8,stroke:#888780
    style D fill:#F1EFE8,stroke:#888780
    style E fill:#F1EFE8,stroke:#888780
    style F fill:#F1EFE8,stroke:#888780
```

**This is an API-orchestration project, not a machine-learning project.** You're wiring together existing services — no model training involved.

---

## 📚 Learning Order Suggestion

| Week | Focus | Outcome |
|:----:|-------|---------|
| 1 | REST APIs + JSON in Python | Can call any API |
| 2 | OAuth + Graph API | Can fetch your emails |
| 3 | LLM API + prompting | Can summarize text |
| 4 | Structured output (JSON mode) | Can get usable data back |
| 5 | Put it together | Working Phase 1–2 |
| 6+ | Streamlit | Working GUI |

---

## ✅ Takeaways

- **Five core skills**: Python/JSON, REST APIs, OAuth, LLM calls, structured prompting
- **No ML theory needed** — this is orchestration, not model building
- **OAuth is the hardest early hurdle** — budget time for it
- **Low temperature** for analysis, **higher** for reply variety
- Embeddings and agents are **optional upgrades**, not requirements

---

[← Interface](08-interface.md) · [🏠 Overview](../README.md) · [Next: Build Roadmap →](10-build-roadmap.md)
