# 2 · Where to Run It 🖥️

> **The question this answers:** Jupyter notebook? VS Code? A server somewhere? — This is the clarity you need before writing any code.

[← Architecture](01-architecture.md) · [🏠 Overview](../README.md) · [Next: Connecting to Outlook →](03-connecting-to-outlook.md)

---

## 🤔 The Short Answer

```mermaid
flowchart TD
    Q{What stage<br/>are you at?}
    Q -->|"Exploring / learning"| A["📓 Jupyter Notebook<br/>inside VS Code"]
    Q -->|"Building the real thing"| B["📁 Python project<br/>in VS Code"]
    Q -->|"Want it always-on"| C["☁️ Cloud server<br/>or scheduled task"]

    style Q fill:#FAEEDA,stroke:#BA7517
    style A fill:#EAF3DE,stroke:#639922
    style B fill:#E6F1FB,stroke:#378ADD
    style C fill:#EEEDFE,stroke:#7F77DD
```

**Recommendation:** Start in a **Jupyter notebook inside VS Code**, then graduate to **`.py` files in VS Code** once it works.

---

## 📊 The Three Options Compared

| | 📓 Jupyter Notebook | 📁 VS Code Project | ☁️ Cloud Server |
|---|---|---|---|
| **Best for** | Experimenting, learning | Real application | Always-on automation |
| **See results instantly** | ✅ Yes, cell by cell | ⚠️ Run whole script | ❌ Via logs |
| **Good for a GUI** | ❌ No | ✅ Yes | ✅ Yes |
| **Setup effort** | 🟢 Minimal | 🟡 Moderate | 🔴 High |
| **Runs when laptop off** | ❌ No | ❌ No | ✅ Yes |
| **Start here?** | ✅ **Yes** | Phase 2 | Phase 5+ |

---

## 🧭 The Recommended Progression

```mermaid
flowchart LR
    A["📓 Notebook<br/>Test: can I fetch<br/>5 emails?"] --> B["📓 Notebook<br/>Test: can the LLM<br/>summarize them?"]
    B --> C["📁 VS Code<br/>Move working code<br/>into modules"]
    C --> D["🖥️ Streamlit<br/>Add a GUI"]
    D --> E["☁️ Optional<br/>Deploy / schedule"]

    style A fill:#EAF3DE,stroke:#639922
    style B fill:#EAF3DE,stroke:#639922
    style C fill:#E6F1FB,stroke:#378ADD
    style D fill:#EEEDFE,stroke:#7F77DD
    style E fill:#F1EFE8,stroke:#888780
```

---

## 💡 Why Notebook First?

Connecting to Outlook has **many small steps that can each fail** (app registration, permissions, token, API call). A notebook lets you test **one step at a time** and see exactly where it breaks.

```mermaid
flowchart TD
    A["Cell 1: Import libraries"] -->|"✅ works"| B["Cell 2: Authenticate"]
    B -->|"✅ works"| C["Cell 3: Fetch 1 email"]
    C -->|"❌ fails here"| D["🔍 Fix just this step<br/>without rerunning<br/>everything"]

    style A fill:#EAF3DE,stroke:#639922
    style B fill:#EAF3DE,stroke:#639922
    style C fill:#FBEAF0,stroke:#D4537E
    style D fill:#FAEEDA,stroke:#BA7517
```

---

## ⚙️ Environment Setup (One Time)

```mermaid
flowchart LR
    A["1️⃣ Install<br/>Python 3.10+"] --> B["2️⃣ Install<br/>VS Code"]
    B --> C["3️⃣ Add Python +<br/>Jupyter extensions"]
    C --> D["4️⃣ Create virtual<br/>environment"]
    D --> E["5️⃣ pip install<br/>packages"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#E6F1FB,stroke:#378ADD
    style C fill:#E1F5EE,stroke:#1D9E75
    style D fill:#E1F5EE,stroke:#1D9E75
    style E fill:#EAF3DE,stroke:#639922
```

**Packages you'll need:**

| Package | Purpose |
|---------|---------|
| `msal` | Microsoft authentication |
| `requests` | Calling the Graph API |
| `anthropic` or `openai` | LLM calls |
| `pandas` | Organizing email data |
| `streamlit` | The GUI (later) |

---

## ✅ Takeaways

- **Start in a Jupyter notebook** inside VS Code — test step by step
- **Move to `.py` modules** once each piece works
- **Cloud/server only later**, when you want it running unattended
- Your laptop is enough for everything through Phase 4

---

[← Architecture](01-architecture.md) · [🏠 Overview](../README.md) · [Next: Connecting to Outlook →](03-connecting-to-outlook.md)
