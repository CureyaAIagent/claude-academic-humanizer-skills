---
name: "research_paper_verification_skill"
version: "1.0"
description: >
  Claude skill for end-to-end verification of academic research papers.
  Includes reference & DOI verification, plagiarism detection, AI content
  removal, formatting compliance, and cross-verification with past journal publications.
---

metadata:
  target_journal: "Specify journal here"
  manuscript_title: "Specify title here"
  authors:
    - name: "Author 1"
      affiliation: "Institution 1"
    - name: "Author 2"
      affiliation: "Institution 2"
  keywords: ["keyword1", "keyword2", "keyword3"]
  DOI: "To be verified and corrected"

data_sources:
  - SciSpace
  - Connected Papers
  - Research Rabbit
  - CrossRef
  - PubMed
  - Web of Science
  - Scopus
  - Google Scholar

verification_workflow:
  - step_name: "Initial Manuscript Scan"
    actions:
      - action: "Detect AI-generated content"
        tool: "claude_ai_content_checker"
      - action: "Plagiarism scan"
        tool: "plagiarism_checker"
      - action: "Identify missing or incorrect DOIs"
        tool: "doi_validator"
      - action: "Check table, figure, and caption consistency"
        tool: "table_figure_verifier"
      - action: "Check manuscript formatting compliance"
        tool: "format_checker"

  - step_name: "Reference & DOI Verification"
    actions:
      - action: "Extract references from manuscript"
        tool: "reference_parser"
      - action: "Validate each reference via CrossRef & Scopus"
        tool: "reference_validator"
      - action: "Amend incorrect or missing DOIs"
        tool: "doi_amender"
      - action: "Ensure reference format matches journal guidelines"
        tool: "format_checker"
      - action: "Cross-check references with last 5 published papers"
        tool: "historical_reference_checker"

  - step_name: "Data & Table Verification"
    actions:
      - action: "Verify data consistency in tables"
        tool: "data_validator"
      - action: "Check numerical data and units"
        tool: "data_validator"
      - action: "Validate table format per journal requirements"
        tool: "format_checker"
      - action: "Validate figure legends and captions"
        tool: "table_figure_verifier"

  - step_name: "Content Verification"
    actions:
      - action: "Verify claims and citations using SciSpace & Research Rabbit"
        tool: "citation_verifier"
      - action: "Ensure AI-generated content is rewritten or removed"
        tool: "claude_ai_content_checker"
      - action: "Validate statistical analyses"
        tool: "statistical_validator"
      - action: "Cross-check key results with past 5 journal publications"
        tool: "historical_content_checker"

  - step_name: "Plagiarism & AI Detection"
    actions:
      - action: "Run plagiarism check"
        tool: "plagiarism_checker"
      - action: "Generate plagiarism report"
        output: "plagiarism_report.pdf"
      - action: "Identify AI-generated content"
        tool: "claude_ai_content_checker"
      - action: "Rewrite AI-suspected content where necessary"
        tool: "ai_content_rewriter"

  - step_name: "Formatting & Journal Compliance"
    actions:
      - action: "Check in-text citation formatting"
        tool: "format_checker"
      - action: "Check reference formatting"
        tool: "format_checker"
      - action: "Check headings and subheadings styles"
        tool: "format_checker"
      - action: "Check figure and table placements"
        tool: "format_checker"
      - action: "Check word count compliance"
        tool: "format_checker"
      - action: "Validate supplementary materials formatting"
        tool: "format_checker"

outputs:
  - verified_manuscript: "journal_ready_manuscript.docx/pdf"
  - updated_references: "verified_references.yaml"
  - plagiarism_report: "plagiarism_report.pdf"
  - DOI_corrections: "corrected_DOIs.yaml"
  - AI_content_report: "ai_content_removed_report.pdf"
  - final_verification_summary: "summary_report.yaml"

automation_integration:
  claude_skills:
    - "Reference Verification Skill"
    - "DOI Correction Skill"
    - "Plagiarism Detection Skill"
    - "AI Content Detection & Removal Skill"
    - "Journal Formatting & Compliance Skill"
    - "Data Verification Skill"

version_control:
  last_verified_date: "YYYY-MM-DD"
  verified_by: "Senior Researcher"
  next_review_date: "YYYY-MM-DD"
  version_notes: "Initial full verification template"

