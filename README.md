# 🌿 Daily Reflection Tree

> A deterministic end-of-day reflection tool built for the DeepThought Fellowship Assignment.  
> **No LLM at runtime. Same answers → same path → same reflection. Every time.**

---

## 🚀 How to Run

Click here to open the agent → [agent/index.html](agent/index.html)

To run locally:
1. Click the link above → click **"Raw"** → press **Ctrl+S** → save as `index.html`
2. Double-click the saved file — opens in your browser
3. No internet needed. No API keys. No installation.

---

## 📸 Screenshots

| Start Screen | First Question |
|---|---|
| ![Start](https://raw.githubusercontent.com/shreyashray09/dt-reflection-tree/main/Screenshot%202026-04-27%20170533.png) | ![Question](https://raw.githubusercontent.com/shreyashray09/dt-reflection-tree/main/Screenshot%202026-04-27%20170652.png) |

| Branching in Action | End Screen |
|---|---|
| ![Branching](https://raw.githubusercontent.com/shreyashray09/dt-reflection-tree/main/Screenshot%202026-04-27%20170731.png) | ![End](https://raw.githubusercontent.com/shreyashray09/dt-reflection-tree/main/Screenshot%202026-04-27%20170843.png) |

---

## 📁 Repository Structure

```
dt-reflection-tree/
├── agent/
│   └── index.html              ← The working web agent (open in browser)
├── tree/
│   ├── reflection-tree.json    ← Full tree data (45 nodes, 3 axes)
│   └── tree-diagram.md         ← Visual diagram (paste into mermaid.live)
├── transcripts/
│   ├── persona-1-victor.md     ← Sample run: Victor persona
│   └── persona-2-victim.md     ← Sample run: Victim persona
├── write-up.md                 ← Design rationale + psychology sources
└── README.md                   ← This file
```

---

## 🧠 The Three Axes

### Axis 1 — Locus (Victim ↔ Victor)
Based on Rotter's Locus of Control (1954) and Dweck's Growth Mindset (2006).  
Surfaces whether the employee sees their own agency in the day's events.

### Axis 2 — Orientation (Entitlement ↔ Contribution)
Based on Campbell et al.'s Psychological Entitlement (2004) and Organ's OCB (1988).  
Surfaces whether the employee was tracking what they gave vs. what they were owed.

### Axis 3 — Radius (Self-Centric ↔ Altrocentric)
Based on Maslow's Self-Transcendence (1969) and Batson's Perspective-Taking (2011).  
Surfaces how wide the employee's circle of concern extended during the day.

---

## 🌳 Tree Diagram

View the full branching structure → [`tree/tree-diagram.md`](tree/tree-diagram.md)

Paste the Mermaid code into **[mermaid.live](https://mermaid.live)** to see the full visual diagram.

---

## 📊 Tree Statistics

| Metric | Count |
|---|---|
| Total nodes | 45 |
| Question nodes | 14 |
| Decision nodes | 11 |
| Reflection nodes | 6 |
| Bridge nodes | 6 |
| Unique conversation paths | 16 |

---

## 📄 Sample Transcripts

- [`transcripts/persona-1-victor.md`](transcripts/persona-1-victor.md) — Victor / Contributing / Altrocentric
- [`transcripts/persona-2-victim.md`](transcripts/persona-2-victim.md) — Victim / Entitled / Self-Centric

---

## ✍️ Design Write-Up

Full rationale, psychology sources, and trade-offs → [`write-up.md`](write-up.md)

---

## 👤 Built By

**Shreyash Ray** — DT Fellowship Assignment 2026
