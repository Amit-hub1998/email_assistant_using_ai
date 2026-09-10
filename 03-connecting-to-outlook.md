# 3 · Connecting to Outlook 🔌

> **The question this answers:** How does Python actually get my emails out of Outlook?

[← Where to Run It](02-where-to-run-it.md) · [🏠 Overview](../README.md) · [Next: Fetch & Summarize →](04-fetch-and-summarize.md)

---

## 🚪 The Three Ways In

```mermaid
flowchart TD
    Q["Getting emails<br/>into Python"] --> A["✅ Microsoft Graph API<br/>modern, official<br/>RECOMMENDED"]
    Q --> B["⚠️ IMAP<br/>older, simpler<br/>often disabled by IT"]
    Q --> C["⚠️ Outlook COM<br/>Windows only<br/>needs Outlook open"]

    style Q fill:#FAEEDA,stroke:#BA7517
    style A fill:#EAF3DE,stroke:#639922
    style B fill:#F1EFE8,stroke:#888780
    style C fill:#F1EFE8,stroke:#888780
```

**Use Graph API.** It's Microsoft's official modern route, works from any OS, and doesn't need Outlook installed.

---

## 🔐 How Authentication Works (OAuth 2.0)

You never put your password in code. Instead you get a **token** — a temporary pass.

```mermaid
sequenceDiagram
    participant PY as 🐍 Python App
    participant MS as 🔐 Microsoft Login
    participant U as 👤 You
    participant API as 📧 Graph API

    PY->>MS: "I want mailbox access"
    MS->>U: Show login page
    U->>MS: Sign in + approve
    MS->>PY: Here's your access token 🔑
    PY->>API: Request emails + token
    API->>PY: ✅ Returns emails
```

---

## 🪪 The Setup Steps (One Time)

```mermaid
flowchart TD
    A["1️⃣ Go to Azure Portal<br/>portal.azure.com"] --> B["2️⃣ Register an app<br/>App Registrations"]
    B --> C["3️⃣ Note the IDs<br/>Client ID + Tenant ID"]
    C --> D["4️⃣ Add API permission<br/>Mail.Read"]
    D --> E["5️⃣ Grant consent"]
    E --> F["6️⃣ Use in Python<br/>via MSAL"]

    style A fill:#E6F1FB,stroke:#378ADD
    style B fill:#E6F1FB,stroke:#378ADD
    style C fill:#E1F5EE,stroke:#1D9E75
    style D fill:#FAEEDA,stroke:#BA7517
    style E fill:#FAEEDA,stroke:#BA7517
    style F fill:#EAF3DE,stroke:#639922
```

---

## 🔑 Permissions You'll Need

```mermaid
flowchart LR
    A["Mail.Read"] --> A1["Read your emails<br/>✅ start here"]
    B["Mail.Send"] --> B1["Send replies<br/>⏳ add later"]
    C["Mail.ReadWrite"] --> C1["Mark read, move<br/>⏳ optional"]

    style A fill:#EAF3DE,stroke:#639922
    style A1 fill:#EAF3DE,stroke:#639922
    style B fill:#FAEEDA,stroke:#BA7517
    style B1 fill:#FAEEDA,stroke:#BA7517
    style C fill:#F1EFE8,stroke:#888780
    style C1 fill:#F1EFE8,stroke:#888780
```

**Start with `Mail.Read` only.** Add send permission only when you're ready for the assistant to actually send.

---

## ⚠️ The Corporate Account Reality Check

```mermaid
flowchart TD
    Q{Is this a<br/>work account?}
    Q -->|"Personal"| A["✅ You can self-approve<br/>proceed freely"]
    Q -->|"Corporate"| B["⚠️ IT admin approval<br/>likely needed"]
    B --> C["Ask IT, OR<br/>use a personal account<br/>to learn first"]

    style Q fill:#FAEEDA,stroke:#BA7517
    style A fill:#EAF3DE,stroke:#639922
    style B fill:#FBEAF0,stroke:#D4537E
    style C fill:#E6F1FB,stroke:#378ADD
```

**Important:** Many companies block app registrations on work accounts. If yours does, build and learn on a **personal Outlook/Gmail account** first.

---

## 📥 What You Get Back

The API returns emails as **JSON** — structured data Python can read directly:

| Field | What it holds |
|-------|--------------|
| `subject` | Email subject line |
| `from` | Sender name + address |
| `receivedDateTime` | When it arrived |
| `bodyPreview` | First ~255 chars |
| `body` | Full content |
| `importance` | Sender-set flag |
| `hasAttachments` | True/false |

These fields become your **raw material** for summarizing and prioritizing.

---

## ✅ Takeaways

- Use **Microsoft Graph API** — official and modern
- Auth via **OAuth 2.0 + MSAL**, never store passwords
- One-time setup: **register app → permissions → consent**
- Start with **`Mail.Read`** only
- On a **corporate account, expect an IT approval step**

---

[← Where to Run It](02-where-to-run-it.md) · [🏠 Overview](../README.md) · [Next: Fetch & Summarize →](04-fetch-and-summarize.md)
