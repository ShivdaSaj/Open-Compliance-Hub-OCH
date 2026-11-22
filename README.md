<div align="center">

# 🛡️ Open Compliance Hub (OCH)

**Open-Source Compliance Toolkit**

*One place to map, measure and master every regulation, standard and framework your organisation answers to.*

🌐 **Live portal:** [compliance.sajinshivdas.online](https://compliance.sajinshivdas.online)

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

![Open Compliance Hub landing page](docs/screenshots/landing-hero.png)

</div>

---

## Contents

1. [What is Open Compliance Hub?](#what-is-open-compliance-hub)
2. [Feature overview](#feature-overview)
3. [Landing page and compliance library](#landing-page-and-compliance-library)
4. [Framework tabs: the common layout](#framework-tabs-the-common-layout)
5. [Two modes: Live portal and My assessment](#two-modes-live-portal-and-my-assessment)
6. [UAE IA tab](#uae-ia-tab)
7. [UAE IA in My assessment mode](#uae-ia-in-my-assessment-mode)
8. [ISO/IEC 27001:2022 tab](#isoiec-270012022-tab)
9. [ISO 27001 in My assessment mode](#iso-27001-in-my-assessment-mode)
10. [ISMS Tools (ISO 27001)](#isms-tools-iso-27001)
11. [Reports and exports](#reports-and-exports)
12. [Backup and restore of your assessment](#backup-and-restore-of-your-assessment)
13. [Coming-soon frameworks](#coming-soon-frameworks)
14. [Mobile and responsive design](#mobile-and-responsive-design)
15. [Privacy and security](#privacy-and-security)
16. [How the score is calculated](#how-the-score-is-calculated)
17. [Status values](#status-values)
18. [Credits, data sources and licences](#credits-data-sources-and-licences)
19. [Licence](#licence)
20. [Disclaimer](#disclaimer)

> The screenshots use **demo data** (a fictional "Demo Organisation LLC") to show the features. They do not show any real organisation's compliance posture.

---

## What is Open Compliance Hub?

Open Compliance Hub is a web portal for tracking compliance with security regulations, standards and frameworks. Each framework has its own tab with:

- the full control library, searchable and filterable
- live dashboards that update in real time
- print-ready and Excel reports
- a private **My assessment** mode, where anyone can run their own self-assessment in their browser

Two frameworks are fully built today:

| Framework | Content |
|---|---|
| 🇦🇪 **UAE IA**: UAE Information Assurance Regulation (V1.1) | 15 families (M1–M6 management, T1–T9 technical), 66 categories, **188 controls** with sub-controls, guidance, expected evidence, priority (P1–P4), compliance category, applicability and SoA |
| 🌐 **ISO/IEC 27001:2022** | **30** ISMS clause requirements (clauses 4–10) and **93** Annex A controls in 4 themes, with ISO/IEC 27002:2022 attributes, the 2013 → 2022 transition map, a risk register and a full **ISMS Tools** suite |

PCI DSS, NIST CSF, GDPR, SOC 2, UAE PDPL and ADHICS are listed as **coming soon**.

---

## Feature overview

| Area | Highlights |
|---|---|
| **Landing page** | Animated hero (particle network), rotating framework names, animated counters, searchable and filterable compliance library with tilt-on-hover cards |
| **Framework tabs** | One tab per framework. Sub-tabs: Dashboard, Controls, Reports & tools, Overview; plus ISMS Tools, Risks and 2013 → 2022 for ISO 27001, and the V1.0 Original for UAE IA |
| **Live dashboards** | Compliance gauge, KPI tiles, programme health, status, family, priority, maturity radar, applicability, SoA, heatmap, priority gaps and recent changes. Updates arrive in real time over Server-Sent Events |
| **Controls explorer** | Family → category → control tree with full-text search and filters for family, status, priority, compliance category, applicability, SoA and ISO 27002 attributes; CSV export |
| **My assessment** | Your own assessment, saved in your browser only. Edit status, SoA, evidence, owners, notes and action items; save score snapshots; back up and restore as `.json` |
| **Risk register** | Likelihood × impact register with a 5 × 5 heatmap, treatment, owner, due date and linked controls (ISO 27001) |
| **ISMS Tools** | Gap assessment, SoA workbench, asset inventory, policies and procedures, evidence register, internal audit, corrective actions, management review, KPIs, and 19 downloadable ISMS templates |
| **Reports** | Executive summary, Statement of Applicability, complete control report, gap and remediation report, and the risk register; as PDF (print), styled Excel or CSV |
| **Responsive** | Works on desktop, tablet and phone |

---

## Landing page and compliance library

The landing page opens with an animated hero:

- a particle-network background
- a typewriter line that cycles through the framework names ("Track compliance for ISO/IEC 27001…")
- animated counters for frameworks, live frameworks, controls tracked and the average score

Below the hero, the **Compliance library** lists every framework as a card. Each card shows:

- the framework's icon, name and short description
- its live score ring
- its status and region
- its control count

Filter the cards by type (Regulation, Standard, Framework), by status (Live, Coming soon), or by a free-text search.

![Compliance library](docs/screenshots/framework-library.png)

---

## Framework tabs: the common layout

Every framework page follows the same layout, so once you know one tab you know them all:

- **Header:** icon, name, status pill (Live / Coming soon), category, region, version and last-updated date.
- **Data source switch:** 🌐 **Live portal** or ✏️ **My assessment** (see the next section).
- **Live indicator:** shows "Live updates on" while the real-time connection is active. When the published data changes, the dashboard refreshes by itself.
- **Scope switch:** view *All* controls or one group. For UAE IA the groups are *Management* and *Technical*; for ISO 27001 they are *ISMS clauses* and *Annex A*.
- **Sub-tabs:**

| Sub-tab | What it shows |
|---|---|
| 📊 Dashboard | KPIs and charts for the selected scope |
| 🧾 Controls | Searchable controls explorer |
| 🧰 ISMS Tools | ISO 27001 toolkit (ISO only) |
| ⚠️ Risks | Risk register with heatmap (ISO only) |
| 🔁 2013 → 2022 | Transition mapping (ISO only) |
| 📑 Reports & tools | Reports, exports, backup & restore |
| 📘 Overview | Description of the framework |
| 🗂️ V1.0 Original | The original UAE IAR dashboard page (UAE IA only) |

Charts are interactive. Click a family bar or a heatmap tile and the explorer opens, filtered to those controls.

---

## Two modes: Live portal and My assessment

| | 🌐 Live portal | ✏️ My assessment |
|---|---|---|
| **Data** | The published compliance posture of the portal | Your own organisation's assessment |
| **Where it is stored** | On the server | **Only in your browser** (`localStorage`). Nothing is sent to the server |
| **Editing** | Read-only | Full editing of every control, risk and tool |
| **Dashboards and reports** | Built from published data | Built from your data, live as you edit |
| **Backup** | n/a | Download and restore a `.json` backup at any time |

When you switch to **My assessment** for the first time, you choose how to start:

- 📋 **Start from the published status:** copy the current portal statuses, then adjust them.
- 🆕 **Start a blank assessment:** every control starts as *Not implemented*.
- 📂 **Restore a backup (.json):** from this portal, or from the original UAE IAR dashboard (V1.0).

![Start my assessment](docs/screenshots/my-assessment-start.png)

Once My assessment is on, a **workspace bar** appears under the framework header. It shows:

- how many controls you have changed and the time of the last save
- a field for your **organisation / entity name**
- **💾 Backup**, **📂 Restore** and **↺ Reset** buttons

Each framework keeps its own separate assessment. You can switch back to the Live portal at any time without losing your data.

---

## UAE IA tab

The UAE IA tab holds the complete **UAE Information Assurance Regulation V1.1** control library.

### Dashboard

The dashboard includes:

- **Compliance score** gauge and KPI tiles (applicable, fully implemented, partial, planned, not implemented)
- **Programme health:** implementation rate, fully implemented, documentation and evidence coverage, action items closed, SoA applicable
- **Compliance categories:** a ring per category (risk management, security operation, architecture design, access control, disaster recovery, communications)

![UAE IA dashboard](docs/screenshots/uaeia-dashboard.png)

It also has these charts:

- status distribution (doughnut)
- controls by family (stacked by status)
- by priority (P1 Critical → P4 Low)
- family maturity radar
- Management vs Technical
- applicability
- Statement of Applicability

![UAE IA charts](docs/screenshots/uaeia-dashboard-charts.png)

At the bottom are a **family heatmap** (colour-coded by score), **priority gaps** (the highest-priority controls not yet implemented) and **recently updated** controls.

![UAE IA family heatmap](docs/screenshots/uaeia-dashboard-heatmap.png)

### Controls explorer

The explorer is a tree: family → category → control. Expand a control to see:

- the **control requirement** and **sub-controls**
- **implementation guidance**
- **expected evidence**
- priority, compliance category, applicability and current status

Filter by family, status, priority, compliance category, applicability and SoA. Use **Expand all** and **Collapse all**, or export the filtered list to CSV.

![UAE IA controls explorer](docs/screenshots/uaeia-controls-explorer.png)

### Reports & tools

This sub-tab has the report cards (see [Reports and exports](#reports-and-exports)), backup and restore, and featured utilities.

![UAE IA reports](docs/screenshots/uaeia-reports.png)

### V1.0 Original

The original *UAE IAR self-assessment dashboard* (V1.0) is kept **unchanged** in its own tab. It runs in a secure sandbox, and any self-assessment data you enter there stays in your own browser. Backups from V1.0 can be restored into My assessment in the new portal, and backups from the portal open in V1.0, because both use the same JSON format.

---

## UAE IA in My assessment mode

In My assessment mode, the whole UAE IA tab works on **your own data**. Every chart, KPI and report recalculates as you edit.

### Dashboard on your data

The workspace bar shows your organisation name, the number of controls you changed and when you last saved. The score and charts reflect your assessment, not the published one.

![UAE IA My assessment dashboard](docs/screenshots/uaeia-assess-dashboard.png)

### Assessment history (score snapshots)

Click **📸 Save snapshot** after each review. The **Assessment history** chart then plots your compliance score and fully-implemented rate over time, so you can show progress quarter by quarter.

![UAE IA assessment history](docs/screenshots/uaeia-assess-history.png)

### Control editor

Expand any control to edit:

| Field | Purpose |
|---|---|
| Status | Fully implemented, partially implemented, planned, not implemented, not applicable, not assessed |
| SoA applicability | YES (applicable) or NO (excluded) |
| SoA justification | Why the control is included or excluded |
| Owner and due date | Who is responsible, and by when |
| Status remarks | Short note on the current state |
| Evidence and evidence link | What proves the control and where it lives |
| Entity notes and auditor notes | Separate notes for the organisation and the assessor |
| Action items | To-do list per control with owner, due date and done flag |

You can also change a status straight from the list without opening the control. Changes save automatically.

![UAE IA control editor](docs/screenshots/uaeia-assess-editor.png)

### Reports from your data

In My assessment mode, every report (PDF, Excel and CSV) is generated from your browser data. Excel and CSV files are built on the fly in your browser and never stored on the server.

![UAE IA My assessment reports](docs/screenshots/uaeia-assess-reports.png)

### Backup and restore

Download your whole assessment as `.json` (compatible with the original UAE IAR dashboard), or restore a previous backup.

![UAE IA backup and restore](docs/screenshots/uaeia-assess-backup.png)

---

## ISO/IEC 27001:2022 tab

The ISO tab covers the whole ISMS:

- **30 clause requirements** (C4.1 … C10.2), which are always applicable
- **93 Annex A controls** (A.5.1 … A.8.34), whose applicability is decided in the SoA, in four themes:

| Theme | Controls |
|---|---|
| Organizational (A.5) | 37 |
| People (A.6) | 8 |
| Physical (A.7) | 14 |
| Technological (A.8) | 34 |

### Dashboard

The dashboard has the same KPIs and programme-health panel as UAE IA. Use the scope switch to see **All**, **ISMS clauses** or **Annex A**.

![ISO 27001 dashboard](docs/screenshots/iso-dashboard.png)

It adds ISO-specific charts:

- **controls by clause / theme**, stacked by status
- **family maturity** radar
- **ISO/IEC 27002:2022 attributes:** control type (preventive, detective, corrective), information security properties (confidentiality, integrity, availability), cybersecurity concepts (identify, protect, detect, respond, recover), operational capabilities and security domains

![ISO 27001 attributes](docs/screenshots/iso-attributes.png)

Further down are the clauses vs Annex A split, the SoA gauge and the clause and theme **heatmap**.

![ISO 27001 heatmap](docs/screenshots/iso-dashboard-more.png)

Three more cards follow:

- **New in 2022:** progress on the 11 controls added in 2022 (A.5.7, A.5.23, A.5.30, A.7.4, A.8.9, A.8.10, A.8.11, A.8.12, A.8.16, A.8.23, A.8.28)
- **Risk register mini-map:** a likelihood × impact heatmap with counts by level
- **ISMS tools:** progress across the toolkit

![ISO 27001 new in 2022, risks and tools](docs/screenshots/iso-history-tools-card.png)

### Controls explorer with 27002 attributes

The explorer has the usual filters, plus filters for:

- **new in 2022**
- **control type**
- **security properties**
- **cybersecurity concepts**
- **operational capabilities**
- **security domains**

Each control lists its **related controls** and the **ISO 27001:2013** controls it replaces, as clickable links.

![ISO 27001 controls explorer](docs/screenshots/iso-controls-scope.png)

### 2013 → 2022 transition

This sub-tab is for organisations moving from ISO 27001:2013 to 2022. Each 2022 control is shown with its 2013 predecessors and the type of change:

| Change type | Count |
|---|---|
| Direct | 71 |
| Merged | 42 |
| Renamed | 1 |
| New in 2022 | 11 |

In total, 114 controls from 2013 map onto the 93 controls of 2022. Search by a 2013 ID (for example `A.12.6.1`) to find where it went, filter by change type, and export the map to CSV.

![ISO 27001 transition](docs/screenshots/iso-transition.png)

---

## ISO 27001 in My assessment mode

Everything in the ISO tab is editable in My assessment mode: control statuses and SoA decisions, the risk register, and every ISMS tool. All of it is saved in your browser and included in your `.json` backup.

### Dashboard on your data

![ISO 27001 My assessment dashboard](docs/screenshots/iso-assess-dashboard.png)

### Assessment history and tools progress

Save score snapshots after each review. The history chart then tracks your score over time, alongside progress for each ISMS tool.

![ISO 27001 assessment history](docs/screenshots/iso-assess-history.png)

### Control editor

The control editor works the same way as in UAE IA: status, SoA applicability and justification, owner, due date, evidence, notes and action items. It works for both clauses and Annex A controls.

![ISO 27001 control editor](docs/screenshots/iso-assess-editor.png)

### Risk register

Build your own risk register. Each risk records:

- asset, threat and vulnerability
- **likelihood** and **impact** (1–5), which give the score and level (Low, Medium, High, Critical)
- **treatment** (mitigate, transfer, avoid, accept), status, owner and due date
- **linked Annex A controls**, which are clickable
- notes or a treatment plan

The **heatmap** shows open risks by likelihood × impact. Filter by level, status or treatment, import risks from CSV, and export to CSV or PDF.

![ISO 27001 risk register](docs/screenshots/iso-risk-register.png)

![Add risk](docs/screenshots/iso-assess-add-risk.png)

### Reports from your data

Generate every report from your own assessment, including the risk register report.

![ISO 27001 My assessment reports](docs/screenshots/iso-assess-reports.png)

### Backup and restore

![ISO 27001 backup](docs/screenshots/iso-assess-backup.png)

---

## ISMS Tools (ISO 27001)

The **🧰 ISMS Tools** sub-tab groups the tools by the Plan-Do-Check-Act cycle of an ISMS. Each tool card shows its clause or control references and your progress.

![ISMS Tools](docs/screenshots/iso-isms-tools.png)

| Phase | Tool | What it does |
|---|---|---|
| **Plan** | 🧭 Gap assessment | 39 questions across clauses 4–10 and key Annex A areas. Answer *Yes*, *Partially*, *No* or *N/A*, add the document reference and comments, and get a readiness score per section. You can push the answers into control statuses with **Apply to controls** |
| **Plan** | 📋 Statement of Applicability | Workbench for all 93 Annex A controls: applicability, justification, maturity level (Pending, Absent, In Progress, Established, Operational…) and status. Export to CSV, PDF or Excel |
| **Plan** | ⚠️ Risk register | Opens the Risks tab |
| **Plan** | 🗄️ Asset inventory | Information assets with type, owner, location, classification, criticality and related controls |
| **Support** | 📚 Policies & procedures | Register of mandatory documented information, policies and procedures, with owner, version and review status |
| **Support** | 📎 Evidence register | Evidence for controls and requirements: type, location or link, owner, collection and expiry dates |
| **Check** | 🔍 Internal audit | Audit checklist with result (conforming, observation, OFI, minor or major nonconformity), evidence reviewed and findings. Raise a corrective action from a nonconformity in one click |
| **Check** | 🏛️ Management review | Review meetings: inputs covered (9.3.2), decisions and actions (9.3.3) |
| **Check** | 📈 Performance measurement | KPIs with measurement type, threshold, current value and follow-up |
| **Act** | 🛠️ Corrective actions | Nonconformities and improvements with root cause, action, owner, due date and status |
| **Library** | 📦 ISMS template library | 19 downloadable Word and Excel templates |

Every register supports **add, edit and delete**, **search and filter**, **CSV import and export**, and a **PDF** report. Some registers come with suggested starting rows (for example, the internal audit checklist starts with 34 items) that you can keep, edit or delete.

### Gap assessment

![Gap assessment](docs/screenshots/iso-gap-assessment.png)

### Statement of Applicability workbench

![SoA workbench](docs/screenshots/iso-soa-workbench.png)

### Asset inventory

![Asset inventory](docs/screenshots/iso-asset-register.png)

### Internal audit

![Internal audit](docs/screenshots/iso-internal-audit.png)

### ISMS template library

Download ready-to-edit templates from the **ISO 27001:2022 Toolkit**:

| Group | Templates |
|---|---|
| Gap Assessment Plan | Gap Assessment Plan (XLSX), Guidance on Gap Assessment (DOCX) |
| SOA | Statement of Applicability with Implementation Status (XLSX) |
| Risk Register | Risk Register (XLSX), Guidance for Completing Risk Register (DOCX) |
| Scope and Context | Scope (DOCX) |
| Asset Inventory | Asset Inventory (XLSX) |
| BC / DR | Business Continuity Plan (DOCX), Disaster Recovery Plan (DOCX) |
| Policy | Information Security Policy and Procedures (DOCX) |
| Awareness | Awareness and Training Plan (DOCX) |
| Management Review | Management Review Meeting (DOCX), Performance Measurement and Findings (XLSX) |
| ISMS Checklists | ISMS Implementation Checklist, Information Risk Checklist, Mandatory ISMS Documentation Checklist (DOCX) |
| Internal Audit | Internal Audit Plan (DOCX), Internal Audit Checklist (XLSX) |
| ROI | Return on Investment (DOCX) |

![ISMS template library](docs/screenshots/iso-template-library.png)

---

## Reports and exports

The **📑 Reports & tools** sub-tab offers:

| Report | Contents | Formats |
|---|---|---|
| 📈 Executive summary | One-page overview: score, status mix, families, priorities, compliance categories and top gaps | PDF |
| 📋 Statement of Applicability | Applicability and justification with implementation status for every control | PDF · Excel · CSV |
| 📚 Complete control report | Every control with all its fields: requirement, guidance, evidence, notes and action items | PDF · Excel · CSV |
| 🎯 Gap & remediation report | Applicable controls not yet fully implemented, ordered by priority (P1 Critical first) | PDF · Excel · CSV |
| ⚠️ Risk register (ISO) | Risks with scores, treatment, owners and linked controls | PDF · CSV |
| 🧰 Tool reports (ISO) | Each ISMS tool's register | PDF · CSV · Excel (SoA) |

**PDF** opens a print-ready page; use *Save as PDF* in the print dialog. **Excel** reports are styled and include a summary sheet. In My assessment mode, all reports come from your own data.

![Executive summary report](docs/screenshots/report-executive.png)

![Statement of Applicability report](docs/screenshots/report-soa.png)

---

## Backup and restore of your assessment

- **💾 Backup:** downloads your assessment for the current framework as `.json`. The file includes control statuses, SoA decisions, notes, evidence, action items, risks, score history and ISMS tool data.
- **📂 Restore:** loads a backup file. It replaces the assessment currently in your browser.
- **↺ Reset:** clears your local assessment for that framework.
- **V1.0 compatible:** UAE IA backups use the same format as the original UAE IAR dashboard, so backups move freely between the two.

> Your assessment lives only in your browser. If you clear site data, or use a different browser or device, it will not be there. **Download a backup regularly.**

---

## Coming-soon frameworks

Frameworks that are not built yet have an animated *Coming soon* page with a short description. They also appear in the library with a **Soon** badge.

![Coming soon](docs/screenshots/coming-soon.png)

---

## Mobile and responsive design

The whole portal adapts to smaller screens, including the landing page, dashboards, explorer, tools and reports.

<p align="center">
  <img src="docs/screenshots/mobile-landing.png" alt="Mobile landing" width="300">
  &nbsp;&nbsp;
  <img src="docs/screenshots/mobile-dashboard.png" alt="Mobile dashboard" width="300">
</p>

---

## Privacy and security

- **My assessment never leaves your browser.** There is no account to create, and nothing you enter is uploaded. Reports built from your data are generated in your browser.
- **Published notes stay private by default.** Entity and auditor notes, evidence links, owners and ISMS tool records in the published data are not shown publicly unless the portal chooses to publish them.
- **Imported pages are sandboxed.** The original V1.0 page runs in a sandbox with a strict Content-Security-Policy. It cannot read the portal's cookies or call its API, and only trusted script hosts are allowed.
- **No third-party tracking scripts.**

---

## How the score is calculated

```
Compliance score = (fully implemented + ½ × partially implemented) ÷ (all controls − not applicable)
```

- **Implementation rate** uses the same formula on applicable controls.
- **Fully implemented %** counts only fully implemented controls.
- **Documentation coverage** is the share of controls with evidence or notes recorded.
- **Gap assessment readiness** scores Yes = 1, Partially = ½, No = 0, and leaves out N/A.

## Status values

| Status | Meaning |
|---|---|
| 🟢 Fully implemented | Control is in place and operating |
| 🟠 Partially implemented | Some elements are in place |
| 🟣 Planned | Scheduled on the roadmap |
| 🔴 Not implemented | Gap: nothing in place |
| ⚪ Not applicable | Excluded (with SoA justification) |
| 🔵 Not assessed | Not reviewed yet |

Imports and restores also recognise common synonyms (*Yes / Partial / No / N/A / Compliant / In progress…*).

---

## Credits, data sources and licences

- **UAE IA control library:** UAE Information Assurance Regulation V1.1, from the original *Open Compliance Hub, UAE IAR Dashboard* (V1.0) by Sajin Shivdas.
- **ISO/IEC 27001:2022 dataset:** control titles, paraphrased descriptions, ISO/IEC 27002:2022 attributes and the 2013 → 2022 mapping come from the MIT-licensed seed data of [sushegaad/MCP-Server-for-ISO27001](https://github.com/sushegaad/MCP-Server-for-ISO27001). One upstream error was corrected: 5.28 is not new in 2022.
- **ISMS templates:** the *ISO 27001:2022 Toolkit* by **Pehan Gunasekara**, MIT licence. The templates are provided unchanged, and each one has a licence link in the portal. Some toolkit files use 2013 Annex A numbering; the interactive tools use the corrected 2022 references.
- **Charts:** [Chart.js](https://www.chartjs.org/) (MIT).

**ISO copyright:** ISO/IEC 27001 and ISO/IEC 27002 are copyrighted by ISO and IEC. This portal contains only control identifiers, titles and paraphrased descriptions, never the normative text of the standards. Buy the official standards from [iso.org](https://www.iso.org/standard/27001) or your national standards body.

---

## Licence

This project is released under the [MIT License](LICENSE) © 2026 Sajin Shivdas.

Third-party content keeps its own licence: the ISO 27001 dataset ([sushegaad/MCP-Server-for-ISO27001](https://github.com/sushegaad/MCP-Server-for-ISO27001)) and the ISO 27001:2022 Toolkit templates (Pehan Gunasekara) are both MIT-licensed, and Chart.js is MIT-licensed. ISO/IEC standards themselves remain the copyright of ISO and IEC.

---

## Disclaimer

Open Compliance Hub is a self-assessment and tracking aid. It does not give legal advice and it is not a certification. Always check requirements against the official text of each regulation or standard and with your auditors or regulator.

---

<div align="center">

**Open Compliance Hub** · Open-Source Compliance Toolkit

Made by [Sajin Shivdas](https://sajinshivdas.com/cybersecurity/)

</div>
