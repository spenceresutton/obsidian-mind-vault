---
description: "Export approved Navigator sanity test cases to a new Google Doc, matching the St. Joseph Sanity Test document formatting exactly — H3 case headers, bold labels, center-aligned lab tables, nested Expected Output bullets."
---

Export approved Navigator sanity test cases to a new Google Doc matching the St. Joseph Sanity Test document format.

**Arguments (optional):** disease state(s) or case numbers to export (e.g., `HAP`, `CAP`, `UTI`, `HAP-14 HAP-15`). If none, export all approved cases. Add `pending` to export from the review queue instead of the approved set (e.g., `pending SSTI`, `pending DFI`) — useful for sharing cases out for review before they're approved.

$ARGUMENTS

---

## Step 1 — Load Cases

Read all `.md` files from `reference/Navigator/Cases/approved/` (or `reference/Navigator/Cases/pending/` if `pending` is passed). Filter by `disease_state` or `case_number` frontmatter if arguments are provided. Sort by `case_number` ascending.

**Distinguishing SSTI vs DFI:** diabetic-foot-infection cases share `disease_state: "SSTI"` and the SSTI case-number sequence, but carry a `dfi` tag and a `dfi-` filename prefix. To split them, filter on the filename prefix (`ssti-` vs `dfi-`), not `disease_state`.

---

## Step 2 — Transform Each Case to HTML

For each case, generate an HTML block using the exact structure below. This HTML will be uploaded to Google Drive and converted to a Google Doc. The formatting must match the target document: **Arial body text, Heading 3 case titles, bold labels, center-aligned tables, nested bullet Expected Output.**

### 2a. Case Header

```html
<h3><b>PNA Case 14: HAP with ESBL History</b></h3>
```

Use the case title from the `# ` heading in the vault note (strip the `#`).

### 2b. Metadata

```html
<p><b>Difficulty:</b> Medium</p>
<p><b>Author:</b> Spencer Sutton</p>
```

Capitalize the difficulty value from frontmatter (e.g., `medium` → `Medium`).

### 2c. Prompt Label

```html
<p><b>Prompt:</b></p>
```

### 2d. Prompt Narrative

Each paragraph in the `## Prompt` section becomes its own `<p>` tag. Preserve italicized organism names (`*Klebsiella pneumoniae*` → `<i>Klebsiella pneumoniae</i>`).

### 2e. Vitals Line

The vitals line (starts with "Vitals") renders as a plain paragraph:

```html
<p>Vitals (hospital day 8): T 39.0°C, HR 108, BP 110/72, RR 24, SpO2 93% on 4L NC.</p>
```

### 2f. Demographics Line

The `Ht: ... Wt: ... BMI: ...` line uses bold labels. Use `&nbsp;&nbsp;&nbsp;` for the three-space separators:

```html
<p><b>Ht:</b> 5'4"&nbsp;&nbsp;&nbsp;<b>Wt:</b> 72 kg&nbsp;&nbsp;&nbsp;<b>BMI:</b> 27.5&nbsp;&nbsp;&nbsp;<b>Baseline SCr:</b> 0.9 mg/dL&nbsp;&nbsp;&nbsp;<b>Allergies:</b> NKDA</p>
```

### 2g. Imaging Section

Section label is plain (not bold, not a heading). Image type sub-header is bold:

```html
<p>Imaging</p>
<p><b>Chest X-Ray — PA and Lateral</b></p>
<p>1. New right lower lobe consolidation, not present on post-operative day 1 film.</p>
<p>2. No cavitary lesion or pleural effusion identified.</p>
<p>3. Cardiac silhouette within normal limits. No pulmonary vascular congestion.</p>
<p>4. Impression: New right lower lobe consolidation consistent with hospital-acquired pneumonia in the appropriate clinical context. Clinical correlation recommended.</p>
```

For portable/bedside CXR: `<p><b>Chest X-Ray — Portable AP</b></p>`

### 2h. Culture Results Section

Section label is plain. Each culture result is a paragraph. Gram stain findings inline:

```html
<p>Culture results</p>
<p>Blood cultures: 2 sets collected — no growth at time of case presentation.</p>
<p>Sputum culture: Pending — purulent sputum sent. Gram stain: gram-negative rods, heavy growth.</p>
<p>Respiratory viral panel: Negative.</p>
<p>MRSA PCR (nasal swab): Negative.</p>
```

**If a susceptibility table is present** (e.g., Case 15 MRSA sensitivities), render it as a 2-column center-aligned table immediately after the organism line:

```html
<p>Sputum culture (48-hour preliminary): <i>Staphylococcus aureus</i> — methicillin-resistant (MRSA). Full susceptibilities pending.</p>
<table border="1" cellpadding="4" cellspacing="0" style="border-collapse:collapse;">
  <tr>
    <td align="center"><b>Antibiotic</b></td>
    <td align="center"><b>Result</b></td>
  </tr>
  <tr><td align="center">Oxacillin</td><td align="center">R</td></tr>
  <tr><td align="center">Vancomycin</td><td align="center">S (MIC 1 µg/mL)</td></tr>
  <tr><td align="center">Linezolid</td><td align="center">S</td></tr>
  <tr><td align="center">Clindamycin</td><td align="center">R</td></tr>
  <tr><td align="center">TMP/SMX</td><td align="center">S</td></tr>
</table>
```

### 2i. CBC Table

Section label is plain. All columns center-aligned:

```html
<p>Complete blood count (CBC with differential)</p>
<table border="1" cellpadding="4" cellspacing="0" style="border-collapse:collapse;">
  <tr>
    <td align="center"><b>Test</b></td>
    <td align="center"><b>Result</b></td>
    <td align="center"><b>Reference range</b></td>
  </tr>
  <tr><td align="center">WBC</td><td align="center">16.2 k/µL</td><td align="center">4.5 – 11.0 k/µL</td></tr>
  <tr><td align="center">Neutrophils (abs.)</td><td align="center">13.9 k/µL</td><td align="center">1.8 – 7.7 k/µL</td></tr>
  <!-- ... all rows ... -->
</table>
```

### 2j. CMP Table

Sub-group labels (Electrolytes, Liver function, Minerals/Calcium) are plain-text rows spanning the table inline — second and third cells left empty:

```html
<p>Comprehensive metabolic panel (CMP)</p>
<table border="1" cellpadding="4" cellspacing="0" style="border-collapse:collapse;">
  <tr>
    <td align="center"><b>Test</b></td>
    <td align="center"><b>Result</b></td>
    <td align="center"><b>Reference range</b></td>
  </tr>
  <tr><td align="center">Electrolytes</td><td align="center"></td><td align="center"></td></tr>
  <tr><td align="center">Sodium</td><td align="center">136 mEq/L</td><td align="center">136 – 145 mEq/L</td></tr>
  <!-- ... electrolyte rows ... -->
  <tr><td align="center">Liver function</td><td align="center"></td><td align="center"></td></tr>
  <!-- ... LFT rows ... -->
  <tr><td align="center">Calcium</td><td align="center"></td><td align="center"></td></tr>
  <tr><td align="center">Calcium (total)</td><td align="center">8.6 mg/dL</td><td align="center">8.5 – 10.5 mg/dL</td></tr>
</table>
```

**Trailing single-row lab tables:** some cases append a lone value (e.g. `| HbA1c | 8.6% | < 5.7% |`) as its own one-row markdown table after the Sepsis Markers table, with no `Test`/`Result` header. Render its cells as a **plain data row, not a bold header** — only bold a table's first row when it actually reads like a header (contains `Test`, `Antibiotic`, `Organism`, or `Result`). Likewise, a one-row 2-column culture table (e.g. `| Organism | Staph aureus (MSSA) |`) should render as a plain `label: value` paragraph, not a bold-header table.

### 2k. Sepsis Markers Table

```html
<p>Sepsis markers</p>
<table border="1" cellpadding="4" cellspacing="0" style="border-collapse:collapse;">
  <tr>
    <td align="center"><b>Test</b></td>
    <td align="center"><b>Result</b></td>
    <td align="center"><b>Reference range</b></td>
  </tr>
  <tr><td align="center">Lactate</td><td align="center">1.8 mmol/L</td><td align="center">&lt; 2.0 mmol/L</td></tr>
  <tr><td align="center">Procalcitonin</td><td align="center">6.8 ng/mL</td><td align="center">&lt; 0.25 ng/mL</td></tr>
  <tr><td align="center">CRP</td><td align="center">201 mg/L</td><td align="center">&lt; 10 mg/L</td></tr>
</table>
<p><i>Resulted: hospital day 8</i></p>
```

### 2l. Expected Output

Label is bold. Each module is a top-level `<li>`. Sub-items are nested `<ul><li>`:

```html
<p><b>Expected Output:</b></p>
<ul>
  <li><b>Presentation:</b> Hospital-acquired pneumonia with ESBL history.</li>
  <li><b>Antibiotic Initiation</b> <i>(if applicable):</i>
    <ul>
      <li>Meropenem 1g q8h</li>
      <li>Comment that MRSA coverage is not indicated given negative MRSA nasal PCR</li>
      <li>Comment that recent ESBL history warrants empiric coverage with a carbapenem</li>
      <li>Treatment duration is 7 days</li>
    </ul>
  </li>
  <li><b>Treatment Optimization</b> <i>(if applicable):</i>
    <ul>
      <li>If culture returns ESBL-producing organism: continue meropenem for 7 days</li>
      <li>If ESBL is susceptible to a fluoroquinolone or TMP/SMX and the infection is monomicrobial: reasonable to convert to oral therapy when afebrile, hemodynamically stable, and without leukocytosis</li>
      <li>If culture returns a non-ESBL organism: de-escalate to an appropriate agent based on susceptibility results</li>
    </ul>
  </li>
</ul>
```

### 2m. Case Separator

Add spacing between cases — three empty paragraphs:

```html
<p><br></p>
<p><br></p>
<p><br></p>
```

---

## Step 3 — Assemble Full HTML Document

Wrap all case blocks in a body with Arial font and 1.5 line height, matching Google Docs defaults:

```html
<!DOCTYPE html>
<html>
<body style="font-family: Arial, sans-serif; font-size: 11pt; line-height: 1.5; color: #000000;">

<!-- Case blocks here -->

</body>
</html>
```

Use HTML entities for special characters: `&lt;` for `<`, `&gt;` for `>`, `µ` for µ, `²` for ², `°` for °. Preserve em dashes as `—` (literal or `&#8212;`).

---

## Step 4 — Create Google Doc via Drive MCP

Use `mcp__claude_ai_Google_Drive__create_file`:

```
title:           "Navigator Cases Export — {disease_state} — {YYYY-MM-DD}"
textContent:     [the assembled HTML string]
contentMimeType: "text/html"
```

**Conversion caveat (verified 2026-06-03):** this Drive tool does **not** auto-convert `text/html` to a native Google Doc — it only auto-converts `text/plain` → Doc and `text/csv` → Sheet. The file uploads as a raw `.html` file (the response and `get_file_metadata` show `mimeType: text/html` and a `/file/d/.../view` URL). Setting the deprecated `mimeType: application/vnd.google-apps.document` target does **not** force conversion either. The `.html` file is still fully usable: opening it in Drive and choosing **File → Open with → Google Docs** renders all formatting (tables, bold, headings) into an editable Doc. Don't claim the link is a Google Doc — it's an HTML file that converts on open.

A `.docx` (built via python-docx from the same parsed model) opens directly in Google Docs with formatting intact and avoids the open-with step, but base64-encoding a multi-case `.docx` is too large to round-trip through the tool call. Prefer the HTML path.

---

## Step 5 — Report

Output:
- Number of cases exported by disease state
- Title of the created file and its link (from `viewUrl`/`webViewLink` in the tool response)
- **Tell the user it's an HTML file, not a Doc**: to read/copy with formatting, open the link → **File → Open with → Google Docs**
- Then copy the case blocks into the target St. Joseph doc (`1x0S5mV4_IvrhFONpMJVz5UJahj6darYBLfLHUEIH2C4`) at the appropriate position
- Flag any junk/test files created during the run for manual deletion (no Drive delete tool is exposed)

---

## Format Reference — What Each Section Looks Like in the Target Doc

| Element | Format |
|---------|--------|
| Case title | H3, bold inside: `### **PNA Case N: Title**` |
| Difficulty / Author | Bold label, plain value |
| Prompt label | Bold: `**Prompt:**` |
| Narrative paragraphs | Plain Arial 11pt |
| Vitals | Plain paragraph, inline with narrative |
| Demographics | Bold labels (`**Ht:**`, `**Wt:**`, etc.), 3-space separated |
| Imaging label | Plain (not bold, not heading) |
| Image type | Bold: `**Chest X-Ray — PA and Lateral**` |
| CXR findings | Numbered plain paragraphs |
| Culture label | Plain (not bold, not heading) |
| Susceptibility table | 2-col, center-aligned |
| CBC / CMP / Sepsis labels | Plain (not bold, not heading) |
| Lab tables | 3-col, center-aligned; sub-group rows have empty cells 2 and 3 |
| Resulted line | Italic |
| Expected Output label | Bold: `**Expected Output:**` |
| Module labels | Bold + italic modifier: `**Antibiotic Initiation** *(if applicable):*` |
| Sub-items | Nested bullet list |
| Between cases | 3 blank lines |
