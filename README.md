# Daily Reflection Tree
A deterministic end-of-day reflection tool. No LLM at runtime. Same answers → same path → same reflection. Every time.
## Screenshots

![Start](Screenshot_2026-04-27_170533.png)
![Question](Screenshot_2026-04-27_170652.png)
![End](Screenshot_2026-04-27_170843.png)
## Structure
```
/tree/
  reflection-tree.json     ← Part A: full tree data (45 nodes)
  [tree-diagram.md](http://tree-diagram.md)          ← Part A: Mermaid visual diagram
/agent/
  index.html               ← Part B: browser-based agent (no server needed)
/transcripts/
  [persona-1-victor.md](http://persona-1-victor.md)      ← Victor / Contributing / Altrocentric path
  [persona-2-victim.md](http://persona-2-victim.md)      ← Victim / Entitled / Self-Centric path
[write-up.md](http://write-up.md)                ← Design rationale (2 pages)
[README.md](http://README.md)                  ← This file
```
## Running the Agent
Open `agent/index.html` in any modern browser. No server, no dependencies, no API keys.
The agent loads the tree logic embedded in the HTML file and walks it deterministically. Every question has fixed options. Every option routes to a known next node. No LLM is called.
## Reading the Tree
The tree is in `tree/reflection-tree.json`. Each node has:
| Field | Purpose |
|---|---|
| `id` | Unique identifier |
| `parentId` | Parent node (for hierarchy) |
| `type` | `start`, `question`, `decision`, `decision_state`, `reflection`, `bridge`, `summary`, `end` |
| `text` | What the employee sees. `{NODE_ID}` is interpolated with that node's answer |
| `options` | For `question`: array of fixed choices. For `decision`: routing rules |
| `target` | Override jump target (used by bridges) |
| `signal` | What this node records in state (`axis1:internal`, etc.) |
| `axis` | Which axis (1, 2, 3) this node belongs to |
### Decision nodes
Regular `decision` nodes match against the answer from their parent question:
```json
"options": [
  ["Sunny", "Cloudy", "A1_Q_AGENCY_HIGH"],
  ["Stormy", "Foggy",  "A1_Q_AGENCY_LOW"]
]
```
Each sub-array: `[match_value1, ..., target_node_id]`.
`decision_state` nodes match against accumulated signal tallies:
```json
"options": [
  ["axis1", "internal", "A1_R_INTERNAL"],
  ["axis1", "external", "A1_R_EXTERNAL"]
]
```
Routes to whichever pole has accumulated more signals on that axis.
### Signals
Every `question` and `reflection` node optionally carries a `signal` tag. When the employee passes through that node, the tally increments:
```
axis1:internal → state.signals.axis1.internal++
axis2:contribution → state.signals.axis2.contribution++
```
The `decision_state` nodes read the dominant pole (whichever side has more) and route accordingly.
## Tree Statistics
| Metric | Count |
|---|---|
| Total nodes | 45 |
| Question nodes | 14 |
| Decision nodes | 11 |
| Reflection nodes | 6 |
| Bridge nodes | 6 |
| Start/Summary/End | 3 |
| Axes covered | 3 (all, in sequence) |
| Options per question | 4 |
| Unique conversation paths | 16 |
## The Three Axes
**Axis 1 — Locus (Victim ↔ Victor)**
Based on Rotter's Locus of Control (1954) and Dweck's Growth Mindset (2006). Surfaces whether the employee sees their own agency in the day's events.
**Axis 2 — Orientation (Entitlement ↔ Contribution)**
Based on Campbell et al.'s Psychological Entitlement (2004) and Organ's OCB (1988). Surfaces whether the employee was tracking what they gave vs. what they were owed.
**Axis 3 — Radius (Self-Centric ↔ Altrocentric)**
Based on Maslow's Self-Transcendence (1969) and Batson's Perspective-Taking (2011). Surfaces how wide the employee's circle of concern extended during the day. 
