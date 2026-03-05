---
name: journal-reference-citation-validator
description: Validates references and in-text citations in research manuscripts to ensure compliance with journal author guidelines, detect citation mismatches, identify missing references, verify DOI links, and correct formatting according to required citation styles.
version: "1.0"
author: CUREEYA
---

# Journal Reference Citation Validator

## Purpose

Ensures that all references and in-text citations in a research manuscript comply with academic publishing standards and the author guidelines of target journals.

The system verifies citation accuracy, reference completeness, DOI validity, formatting consistency, and alignment with required citation styles.

## Core Responsibilities

- Detect incorrect citation formatting  
- Verify citation–reference matching  
- Identify missing references  
- Detect unused references  
- Validate citation style compliance  
- Ensure references follow journal author guidelines  
- Verify DOI validity and accessibility  
- Recommend corrected citation formatting  

## Citation Detection

The system scans the manuscript and extracts all in-text citations.

Supported citation formats include:

- Author–Year format (APA, Harvard)
- Numerical citations (IEEE, Vancouver)
- Footnote citations (Chicago, MLA)

## Reference Extraction

The validator extracts the complete reference list and analyzes each entry.

Each reference is checked for required components:

- Author names
- Publication year
- Article title
- Journal or book title
- Volume and issue
- Page numbers
- DOI (if available)

## Citation–Reference Matching

The system verifies that every in-text citation corresponds to a reference entry.

Common issues detected include:

- citations present in text but missing from reference list
- references listed but not cited
- incorrect citation numbering
- author–year mismatch
- duplicate references

## DOI Verification

The validator checks the validity of DOI identifiers.

Verification process:

1. Extract DOI from each reference  
2. Validate DOI format  
3. Check DOI availability through official DOI registries  
4. Flag broken or invalid DOI links  
5. Recommend corrected DOI if available  

Example DOI format:

---

## Citation Style Validation

The validator checks whether references follow the required citation style.

Supported styles include:

- APA
- IEEE
- Vancouver
- Harvard
- MLA
- Chicago

Example formatting rules:

APA format example:

Author, A. A. (Year). Title of article. *Journal Name*, Volume(Issue), Pages.

IEEE format example:

[1] A. Author, "Title of article," *Journal Name*, vol. X, no. X, pp. X–X, Year.

---

## Journal Author Guideline Compliance

The system evaluates whether the manuscript references follow formatting requirements specified in the target journal's author guidelines.

Validation includes:

- reference ordering rules
- citation numbering format
- punctuation and spacing standards
- journal name abbreviations
- DOI inclusion policies

---

## Reference Consistency Analysis

The system checks for inconsistencies across the reference list.

Common issues include:

- inconsistent author name formatting
- inconsistent capitalization
- mixed citation styles
- inconsistent journal abbreviations

## Reference Correction Strategy

When formatting issues are detected, the system generates corrected reference entries.

Corrections may include:

- proper author formatting
- corrected punctuation
- consistent citation style
- standardized journal names
- verified DOI insertion

## Output

Reference and Citation Compliance Report

The report includes:

- Total in-text citations  
- Total references  
- Missing references  
- Unused references  
- Formatting inconsistencies  
- Citation style errors  
- DOI validation results  
- Journal guideline compliance status  
- Corrected reference formatting examples  
- Citation correction recommendations  

## Final Result

A manuscript with fully validated references, corrected citation formatting, verified DOI links, and improved compliance with journal submission requirements.
