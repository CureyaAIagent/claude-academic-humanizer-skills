---
name: research-author-journal-communication
description: >
  Generates customized professional emails to research paper authors regarding
  journal verification, Scopus indexing validation, publication timelines,
  APC charges, and document verification requirements. Supports batch email
  generation for multiple authors and papers.
---
version: "1.0"
author: "Research Communication Automation"
category: research-automation

inputs:
  authors:
    type: array
    description: List of authors receiving communication
    items:
      type: object
      properties:
        author_name:
          type: string
        email:
          type: string
        affiliation:
          type: string

  paper_details:
    type: array
    description: Research paper information
    items:
      type: object
      properties:
        paper_title:
          type: string
        research_field:
          type: string
        keywords:
          type: array
          items:
            type: string

  journal_details:
    type: object
    properties:
      journal_name:
        type: string
      publisher:
        type: string
      indexing:
        type: array
        items:
          type: string
      quartile:
        type: string
      issn:
        type: string

  verification_details:
    type: object
    properties:
      scopus_verification_site:
        type: string
        default: "https://www.scopus.com/sources"
      verification_required:
        type: array
        items:
          type: string
        default:
          - Author affiliation verification
          - Research originality check
          - Citation validation
          - Reference formatting
          - Journal indexing confirmation

  publication_details:
    type: object
    properties:
      initial_processing_fee:
        type: string
      apc_fee:
        type: string
      currency:
        type: string
        default: USD
      payment_stage:
        type: string
        default: "Initial verification stage"

  timelines:
    type: object
    properties:
      verification_time:
        type: string
        default: "3–5 working days"
      peer_review_time:
        type: string
        default: "2–4 weeks"
      publication_time:
        type: string
        default: "4–8 weeks"

  communication:
    type: object
    properties:
      contact_person:
        type: string
      organization:
        type: string
      contact_email:
        type: string
      meeting_link:
        type: string
      response_deadline_days:
        type: integer
        default: 5

outputs:
  generated_emails:
    type: array
    description: Customized email drafts for each author

workflow:
  steps:

    - step: verify_paper_topic
      description: >
        Analyze research paper title and keywords to confirm relevance
        to the selected journal scope.

    - step: validate_journal_indexing
      description: >
        Confirm journal indexing through Scopus Sources database
        and other indexing platforms.

    - step: calculate_processing_charges
      description: >
        Identify initial verification charges and full APC based
        on journal policies.

    - step: generate_email_content
      description: >
        Generate personalized email including:
        - Author name
        - Paper title
        - Journal details
        - Scopus verification link
        - Processing charges
        - Publication timelines
        - Required verification documents
        - Communication details

email_template: |

  Subject: Verification & Publication Process for Your Research Paper – {{paper_title}}

  Dear Dr./Prof. {{author_name}},

  Greetings from {{organization}}.

  We have reviewed the preliminary details of your research manuscript titled:

  "{{paper_title}}"

  Based on the research scope and keywords, this paper aligns with the aims
  and scope of the journal:

  Journal: {{journal_name}}
  Publisher: {{publisher}}
  Indexing: {{indexing}}
  Quartile: {{quartile}}
  ISSN: {{issn}}

  Scopus Source Verification:
  {{scopus_verification_site}}

  Our research verification team will perform the following checks before
  submission to the journal:

  • Research topic alignment with journal scope
  • Citation and reference validation
  • Plagiarism screening
  • AI-content verification
  • Author affiliation authentication
  • Formatting as per journal guidelines

  Publication Timelines:

  Initial Verification:
  {{verification_time}}

  Peer Review Process:
  {{peer_review_time}}

  Estimated Publication Timeline:
  {{publication_time}}

  Initial Processing Charges:

  {{initial_processing_fee}} {{currency}}

  (This covers manuscript verification, formatting,
  indexing validation, and pre-submission preparation.)

  Full APC (if accepted by journal):
  {{apc_fee}} {{currency}}

  To proceed with the verification process, kindly share the following:

  1. Final manuscript (Word / LaTeX format)
  2. Author affiliation details
  3. ORCID IDs (if available)
  4. Contact number for communication
  5. Confirmation to proceed with verification

  If required, we can also schedule a short discussion to explain
  the verification and submission process.

  Meeting Link:
  {{meeting_link}}

  Kindly confirm your interest within
  {{response_deadline_days}} days so that we can initiate
  the verification process and reserve the journal slot.

  If you require any additional verification reports
  (Scopus indexing proof, journal metrics, acceptance probability),
  please let us know.

  We look forward to supporting your research publication.

  Best regards,

  {{contact_person}}
  {{organization}}
  Email: {{contact_email}}

automation_features:
  - batch_email_generation
  - paper_topic_validation
  - journal_scope_matching
  - scopus_index_verification
  - apc_fee_calculation
  - automated_author_personalization
  - response_deadline_tracking

recommended_integrations:
  - email_automation_system
  - crm_database
  - scopus_api
  - plagiarism_checker
  - ai_content_detector
  - journal_database

tags:
  - research
  - academic-publishing
  - scopus
  - journal-verification
  - author-communication
  - automation
