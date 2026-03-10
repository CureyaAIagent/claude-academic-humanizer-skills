---
name: research-diagram-toolkit
description: Generates professional, publication-ready academic diagrams and figures that mimic manually created visuals used in peer-reviewed journals.
---

# Research Diagram Toolkit

## Purpose

Provides a structured workflow for creating **journal-grade academic diagrams** that replicate the visual style commonly found in peer-reviewed publications.

The toolkit ensures that figures appear **human-designed, publication-ready, and compliant with academic formatting standards**, avoiding AI-generated aesthetics.

It is designed for use in:

- Research papers
- PhD theses
- Conference publications
- Journal submissions
- Technical reports

---

## Core Principles

### Authenticity
All diagrams must resemble **hand-crafted visuals produced by researchers** using tools such as Microsoft Visio, SmartPLS, PowerPoint, or Adobe Illustrator.

Key rules:

- Avoid AI-style graphics
- Maintain manual spacing and alignment
- Use subtle imperfections typical of human-designed figures

---

### Publication Ready

All visual outputs must meet **journal submission standards**, including:

- High resolution (minimum **600 DPI**)
- Vector-friendly export formats
- Clean typography
- Minimal visual noise

Preferred export formats:

- **PDF (vector)**
- **EPS (LaTeX compatible)**
- **SVG (editable vector)**
- **PNG 600 DPI**

---

### Field Specific

Visualization standards should match **disciplinary expectations**.

Examples:

| Field | Diagram Type |
|------|------|
| Marketing / Sustainability | Conceptual frameworks |
| Management Research | Structural equation models |
| Engineering | System architecture diagrams |
| Data Science | Analytical pipelines |

---

### Reproducibility

All figures must allow **transparent replication** during peer review.

Requirements:

- Clearly labelled constructs
- Documented workflow
- Version control of diagrams
- Editable source files

---

# Engineering Visualizations

## System Architecture Diagrams

Used for illustrating **technical system designs, workflows, and component interactions**.

---

### Tool 1: draw.io (diagrams.net)

**Version:** 20.3+

**Usage**

Ideal for:

- System architecture diagrams
- Flowcharts
- Conceptual frameworks
- Process pipelines

**Humanization Techniques**

To avoid AI-generated appearance:

- Apply manual spacing adjustments
- Slightly offset connector alignment
- Use consistent but manually selected color palettes
- Adjust arrow curvature manually

**Recommended Color Style**

Use muted academic palettes:

| Element | Hex Code | Usage |
|---------|----------|-------|
| Primary | `#2E86AB` | Main components |
| Secondary | `#A23B72` | Supporting elements |
| Accent | `#F18F01` | Highlights |
| Neutral | `#5C5C5C` | Text and borders |

**Export Settings**

- Resolution: 600 DPI (PNG)
- Format: PDF vector
- Fonts: Embedded
- Size: Max 6.875 inches wide

---

### Tool 2: Inkscape

**Version:** 1.3+

**Usage**

Best for:

- Refining automated diagrams
- Adding hand-drawn elements
- Final polishing touches

**Humanization Techniques**

- Introduce slight imperfections in line weights
- Manually adjust path smoothness
- Add subtle texture overlays
- Vary stroke opacity (95-100%)

**Workflow Tips**

1. Import base diagram from draw.io (SVG)
2. Adjust node positions manually
3. Modify stroke properties for organic feel
4. Add hand-annotated notes if needed
5. Export with embedded fonts

---

## Circuit and Signal Processing

### LTspice

**Version:** XVII

**Usage**

For:

- Electronic circuit schematics
- Simulation waveform outputs
- Filter design illustrations

**Professional Touch**

- Use standard IEEE symbols
- Label all components clearly
- Include measurement points
- Export waveforms at high resolution

---

### MATLAB/Simulink

**Version:** R2023b

**Usage**

For:

- Signal flow graphs
- Control system block diagrams
- Algorithm visualization

**Export Best Practices**

- Save as `.fig` for editing
- Export to PDF with vector data
- Use consistent line weights (0.5pt-1pt)
- Include scale bars for measurements

---

### TikZ/LaTeX

**Precision Drawing**

Packages:

- `circuitikz`: Electrical circuits
- `pgfplots`: Data visualization
- `tikz-cd`: Commutative diagrams

**Example Code**

```latex
\begin{tikzpicture}[node distance=2cm]
  \node[draw, rectangle] (input) {Input};
  \node[draw, circle, right of=input] (process) {Process};
  \node[draw, rectangle, right of=process] (output) {Output};
  \draw[->] (input) -- (process);
  \draw[->] (process) -- (output);
\end{tikzpicture}
