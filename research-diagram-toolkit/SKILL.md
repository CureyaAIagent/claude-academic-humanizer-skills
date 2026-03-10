---
  name: research-diagram-toolkit
  overview:"Professional-grade diagram creation system for academic publications"
 --- 
  core_principles:
    authenticity: "Hand-crafted appearance mimicking expert researcher work"
    publication_ready: "Journal acceptance guaranteed with proper formatting"
    field_specific: "Domain-appropriate visualization standards"
    reproducible: "Fully documented workflow for peer review"

  engineering_visualizations:
    
    system_architecture_diagrams:
      tools:
        - name: "draw.io (diagrams.net)"
          version: "20.3+"
          usage: "Block diagrams, flowcharts, system components"
          humanization_techniques:
            - "Manual spacing adjustments"
            - "Custom color schemes matching journal style"
            - "Hand-drawn connector lines for organic feel"
          export_formats:
            - "PDF (vector)"
            - "EPS for LaTeX integration"
            - "PNG at 600 DPI minimum"
      
      - name: "Inkscape"
        version: "1.3+"
        usage: "Refinement of automated diagrams, custom illustrations"
        humanization_techniques:
          - "Slight imperfections in line weights"
          - "Manual path adjustments"
          - "Texture overlays for paper-like appearance"
        export_formats:
          - "PDF with embedded fonts"
          - "SVG for editing flexibility"
          - "EPS for professional printing"

    circuit_and_signal_processing:
      tools:
        - name: "LTspice"
          version: "XVII"
          usage: "Circuit schematics, simulation results"
        
        - name: "MATLAB/Simulink"
          version: "R2023b"
          usage: "Signal flow graphs, control systems"
          
        - name: "TikZ/LaTeX"
          usage: "Precise mathematical diagrams, integration with equations"
          packages:
            - "circuitikz"
            - "pgfplots"
            - "tikz-cd"

  economics_commerce_visualizations:
    
    data_analysis_diagrams:
      tools:
        - name: "R + ggplot2"
          version: "4.3+"
          libraries:
            - "ggplot2"
            - "ggrepel"
            - "patchwork"
            - "gridExtra"
          humanization_approach:
            - "Manual point positioning tweaks"
            - "Custom theme development"
            - "Selective transparency adjustments"
            - "Hand-annotated elements in post-processing"
            
        - name: "Python + matplotlib/seaborn"
          version: "3.8+"
          libraries:
            - "matplotlib"
            - "seaborn"
            - "plotly"
            - "adjustText"
          customization:
            - "rcParams fine-tuning"
            - "Custom colormaps"
            - "Manual legend placement"
            - "Axis label positioning refinement"

    market_analysis_frameworks:
      tools:
        - name: "Lucidchart"
          features:
            - "Template libraries"
            - "Collaborative editing"
            - "Export control options"
          professional_touch:
            - "Custom icon libraries"
            - "Brand color implementation"
            - "Consistent typography hierarchy"

  interdisciplinary_tools:
    
    conceptual_framework_mapping:
      primary_tool: "Miro"
      features:
        - "Whiteboard-style interface"
        - "Template frameworks (SWOT, PESTEL, etc.)"
        - "Integration capabilities"
      publication_workflow:
        - "Export to PDF at high resolution"
        - "Vector editing in Illustrator/Inkscape"
        - "Final touch-up for academic presentation"
        
    network_and_relationship_diagrams:
      tools:
        - name: "Gephi"
          version: "0.9.2"
          applications: "Social networks, citation analysis, supply chains"
          
        - name: "Cytoscape"
          version: "3.9+"
          applications: "Biological pathways, complex system relationships"
          
        - name: "Graphviz"
          applications: "Automated graph layout, programmatic generation"

  professional_workflow_standards:
    
    file_management:
      directory_structure:
        - "raw_data/"
        - "working_files/"
        - "final_exports/"
        - "version_control/"
        - "supplementary_materials/"
        
      naming_convention: 
        pattern: "{figure_number}_{description}_{version}.{extension}"
        example: "fig_03_market_share_analysis_v04.pdf"
        
    quality_assurance:
      checklist:
        - "Resolution check (minimum 600 DPI for print)"
        - "Font embedding verification"
        - "Color mode appropriate for medium (CMYK vs RGB)"
        - "File size optimization without quality loss"
        - "Accessibility compliance (alt text, contrast ratios)"
        - "Cross-platform rendering consistency"

  advanced_techniques:
    
    latex_integration:
      tikz_methodology:
        code_example: |
          \begin{tikzpicture}[node distance=2cm]
            \node[draw, rectangle] (input) {Input};
            \node[draw, circle, right of=input] (process) {Process};
            \node[draw, rectangle, right of=process] (output) {Output};
            \draw[->] (input) -- (process);
            \draw[->] (process) -- (output);
          \end{tikzpicture}
          
      pgfplots_professional:
        code_example: |
          \begin{axis}[
            xlabel={Time},
            ylabel={Value},
            title={Experimental Results},
            grid=major,
            width=12cm,
            height=8cm
          ]
          \addplot+[smooth] table[x=time,y=value] {data.csv};
          \end{axis}

    hybrid_creation_process:
      step_by_step:
        1: "Data preparation and cleaning"
        2: "Initial automated plot generation"
        3: "Manual refinement and adjustment"
        4: "Typography and styling enhancement"
        5: "Integration with document workflow"
        6: "Quality assurance and final export"

  journal_submission_requirements:
    
    common_specifications:
      ieee:
        - "Vector formats preferred (PDF, EPS)"
        - "Minimum 300 DPI for raster elements"
        - "Fonts must be embedded"
        - "Maximum width: 6.875 inches"
        
      nature:
        - "High-resolution vector graphics"
        - "Color figures at 300 DPI minimum"
        - "Black and white versions required"
        - "Supplementary figure files separately"
        
      elsevier:
        - "EPS, PDF, or TIFF formats"
        - "Color space specification required"
        - "Figure captions as separate text"
        - "Source files preservation"

    cross_journal_compatibility:
      universal_standards:
        - "CMYK color mode for print journals"
        - "RGB acceptable for online-only publications"
        - "Open formats preferred over proprietary"
        - "Version control documentation maintained"
        
  expert_tips_for_humanization:
    
    avoiding_automated_appearance:
      techniques:
        - "Introduce slight variations in element spacing"
        - "Use non-uniform line weights intentionally"
        - "Add hand-annotated elements in post-processing"
        - "Include subtle texture overlays"
        - "Avoid perfect geometric alignments"
        - "Vary font weights and styles purposefully"
        
    time_efficient_methods:
      shortcuts:
        - "Template libraries for common diagram types"
        - "Style sheets for consistent appearance"
        - "Batch processing for multiple similar figures"
        - "Keyboard shortcuts mastery"
        - "Pre-defined color palettes per discipline"

  software_ecosystem:
    
    primary_suite:
      vector_graphics: ["Inkscape", "Adobe Illustrator"]
      diagramming: ["draw.io", "Lucidchart", "Miro"]
      data_visualization: ["R/ggplot2", "Python/matplotlib"]
      technical_drawing: ["TikZ/LaTeX", "Graphviz"]
      
    complementary_tools:
      image_editing: "GIMP"
      pdf_management: "Adobe Acrobat Pro"
      version_control: "Git with Git-LFS for large files"
      collaboration: "Overleaf for LaTeX projects"
      
    platform_consistency:
      windows_optimized: "PowerPoint for quick mockups"
      mac_optimized: "Keynote for presentation integration"
      linux_friendly: "All open-source alternatives available"

  documentation_and_reproducibility:
    
    metadata_standards:
      required_fields:
        - "Creation date and author"
        - "Software versions used"
        - "Raw data sources"
        - "Processing steps taken"
        - "Final output specifications"
        
    sharing_protocols:
      git_repository_structure:
        - "README.md explaining methodology"
        - "requirements.txt or environment.yml"
        - "source_data/ directory"
        - "processing_scripts/ directory"
        - "final_figures/ directory"
        - "LICENSE file for reuse permissions"

  validation_checklist:
    
    pre_submission:
      technical_validation:
        - "File opens correctly on multiple systems"
        - "Fonts render properly without substitution"
        - "Colors display accurately across devices"
        - "Resolution meets publisher requirements"
        
      content_validation:
        - "Labels are clear and professionally formatted"
        - "Legend explains all visual elements"
        - "Scale and units are properly indicated"
        - "Copyright permissions secured for any reused elements"
        
      accessibility_compliance:
        - "Contrast ratios meet WCAG standards"
        - "Alternative text descriptions provided"
        - "Colorblind-friendly palette consideration"
        - "Screen reader compatibility checked"
