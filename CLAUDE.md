# Swiss Real Estate Market Research - Web Crawling Task

## Project Overview
Conduct comprehensive web crawling for Swiss real estate market research and generate structured LaTeX files for academic/research purposes.

## Environment Setup
- **Working Directory**: `immo_tool/work/`
- **Virtual Environment**: Activate existing venv or create new one in project directory
- **Output Format**: Structured LaTeX (.tex) files

## Task Requirements

### 1. Initial Setup
```bash
# Navigate to project directory
cd /mnt/d/immo_tool/

# Activate virtual environment
source venv/bin/activate  # or create if doesn't exist

# Read existing files in work directory
ls -la work/
```

### 2. Web Crawling Targets
Focus on Swiss real estate market data from these sources:
- **ImmoScout24.ch** - Property listings and market trends
- **Homegate.ch** - Residential market data
- **Comparis.ch** - Price comparisons and market analysis
- **Swiss Federal Statistical Office** - Official housing statistics
- **UBS Real Estate Bubble Index** - Market analysis reports
- **Credit Suisse Real Estate Monitor** - Market research
- **Swiss National Bank** - Interest rates and housing finance data

### 3. Data Collection Structure
Organize crawled data into these research categories:

#### 3.1 Market Overview
- Current market trends
- Price developments (rental/purchase)
- Regional variations
- Market forecasts

#### 3.2 Property Types Analysis
- Apartments (by room count)
- Single-family homes
- Commercial properties
- New vs. existing properties

#### 3.3 Geographic Analysis
- Canton-level data
- Major cities (Zurich, Geneva, Basel, Bern)
- Urban vs. rural markets
- Transportation impact on prices

#### 3.4 Economic Factors
- Interest rate impact
- Mortgage availability
- Government regulations
- Tax implications

### 4. LaTeX Output Structure

#### 4.1 File Organization
Create/update these files in `immo_tool/work/`:

```
work/
├── main_research.tex           # Main research document
├── sections/
│   ├── market_overview.tex     # Market trends and overview
│   ├── property_analysis.tex   # Property types and pricing
│   ├── geographic_analysis.tex # Regional market differences
│   ├── economic_factors.tex    # Economic influences
│   └── data_appendix.tex       # Raw data tables
├── tables/
│   ├── price_data.tex          # Price comparison tables
│   ├── market_stats.tex        # Statistical summaries
│   └── regional_data.tex       # Geographic breakdowns
└── figures/
    ├── price_charts.tex        # Data visualizations
    └── trend_graphs.tex        # Market trend graphics
```

#### 4.2 LaTeX Template Structure
Each section should follow this template:

```latex
\section{Section Title}
\label{sec:section_label}

% Data source and collection date
\subsection{Data Sources}
\begin{itemize}
\item Source 1: [URL] - Accessed: [Date]
\item Source 2: [URL] - Accessed: [Date]
\end{itemize}

\subsection{Key Findings}
% Summarized findings from web crawling

\subsection{Detailed Analysis}
% Structured analysis with subsections

\subsection{Data Tables}
% Include relevant tables with proper citations

\subsection{Implications}
% Research implications and insights
```

### 5. Directory Reading Protocol
At the beginning of each section generation:

1. **Read existing files**: Check what's already in `immo_tool/work/`
2. **Identify gaps**: Determine what data/sections are missing
3. **Preserve existing work**: Don't overwrite existing content unless explicitly updating
4. **Maintain consistency**: Follow existing naming conventions and structure

### 6. Data Quality Requirements

#### 6.1 Source Verification
- Verify all URLs are accessible
- Document data collection timestamps
- Include source reliability assessment
- Note any limitations or data gaps

#### 6.2 Data Processing
- Clean and standardize data formats
- Convert currencies to CHF where needed
- Standardize date formats (DD.MM.YYYY)
- Handle missing data appropriately

#### 6.3 LaTeX Formatting
- Use proper sectioning hierarchy
- Include labels for cross-referencing
- Format tables with booktabs package
- Include proper citations and references

### 7. Implementation Steps

#### Step 1: Environment Check
```bash
# Check current directory contents
pwd && ls -la work/

# Verify Python environment and packages
python --version
pip list | grep -E "(requests|beautifulsoup|selenium|pandas)"
```

#### Step 2: Web Crawling Implementation
- Install required packages if missing
- Implement respectful crawling (delays, robots.txt compliance)
- Create data collection scripts
- Implement error handling and logging

#### Step 3: Data Processing
- Clean and structure collected data
- Create summary statistics
- Generate comparison tables
- Identify key insights

#### Step 4: LaTeX Generation
- Read existing work directory structure
- Generate/update .tex files according to structure
- Ensure proper LaTeX syntax and compilation
- Create comprehensive bibliography

### 8. Quality Assurance
- Test LaTeX compilation (`pdflatex main_research.tex`)
- Verify all tables and figures render correctly
- Check cross-references work properly
- Validate data accuracy and sources

### 9. Final Deliverables
- Structured .tex files ready for academic use
- Comprehensive data collection documentation
- Clean, compilable LaTeX code
- Source code for web crawling scripts
- Data collection logs and timestamps

## Success Criteria
✅ All .tex files compile without errors  
✅ Data is current (collected within last 30 days)  
✅ Sources are properly documented and cited  
✅ Structure supports future research expansion  
✅ Content provides actionable market insights  

## Notes
- Respect website terms of service and rate limits
- Include data collection methodology in appendix
- Maintain version control for iterative improvements
- Document any challenges or limitations encountered

---

# ⚠️ **CRITICAL: FINAL DIRECTORY INTEGRATION REQUIREMENTS**

## **Updated Project Architecture**

**IMPORTANT**: All .tex files generated in `/mnt/d/immo_tool/work/` MUST be fully compatible with the institutional LaTeX structure in `/mnt/d/immo_tool/final/` for direct Overleaf upload.

### **Final Directory Structure Analysis**
```
final/
├── ht_eit_latex_template.tex    # Main document using report.cls
├── header.tex                   # Centralized package management
├── report.cls                   # Custom FHNW institutional class
├── literature/
│   └── references.bib           # Bibliography file (biblatex format)
├── sections/                    # Section files (currently empty)
└── tables/                      # Table files (currently empty)
```

## **COMPATIBILITY REQUIREMENTS**

### **1. Document Class Compatibility** ⚠️ **CRITICAL CONFLICT**

**Current Work Structure (INCOMPATIBLE):**
```latex
\documentclass[12pt,a4paper]{article}
```

**Required Final Structure:**
```latex
\documentclass{report}
\input{header}  % Uses report.cls (custom FHNW class)
```

**RESOLUTION REQUIRED:**
- All section files must be compatible with `report` document class
- Remove document class declarations from section files
- Ensure sectioning hierarchy works with report class structure

### **2. Package Management System** ⚠️ **CRITICAL CONFLICT**

**Current Work Structure (INCOMPATIBLE):**
- Self-contained package imports in main document
- Individual package loading in each file

**Required Final Structure:**
- Centralized package management through `\input{header}`
- Additional packages loaded in main template file
- No package declarations in section files

**RESOLUTION REQUIRED:**
- Remove ALL `\usepackage{}` statements from section files
- Rely on packages loaded in `header.tex` and main template
- Verify package compatibility with existing final structure

### **3. Bibliography System** ⚠️ **CRITICAL CONFLICT**

**Current Work Structure (INCOMPATIBLE):**
```latex
\begin{thebibliography}{99}
\bibitem{source} Manual bibliography entries
\end{thebibliography}
```

**Required Final Structure:**
```latex
\usepackage[backend=biber, style=apa, natbib=true]{biblatex}
\addbibresource{literature/references.bib}
\printbibliography[heading=bibintoc,title={References}]
```

**RESOLUTION REQUIRED:**
- Convert all manual bibliography entries to `.bib` format
- Use `\cite{}` commands instead of manual citations
- Add entries to `/final/literature/references.bib`

### **4. File Integration Method** ⚠️ **CONFLICT**

**Current Work Structure:**
```latex
\input{sections/filename}
```

**Required Final Structure:**
```latex
\include{sections/filename}
```

**RESOLUTION REQUIRED:**
- Use `\include{}` instead of `\input{}` for section files
- Ensure section files work with page breaking behavior of `\include`

## **UPDATED LATEX TEMPLATE STRUCTURE**

### **4.2 Final-Compatible LaTeX Template** ⚠️ **UPDATED**

Each section file must follow this template (NO document structure elements):

```latex
% NO \documentclass, \usepackage, \begin{document} or \end{document}
% File: sections/section_name.tex

\section{Section Title}
\label{sec:section_label}

\subsection{Data Sources}
\begin{itemize}
\item Source 1: [URL] - Accessed: [Date] \cite{source1_key}
\item Source 2: [URL] - Accessed: [Date] \cite{source2_key}
\end{itemize}

\subsection{Key Findings}
% Content using packages from header.tex

\subsection{Detailed Analysis}
% Analysis content

\subsection{Data Tables}
% CRITICAL: Use correct path syntax for Overleaf compatibility
\input{tables/table_name.tex}

\subsection{Implications}
% Implications and insights
```

### **4.2.1 CRITICAL Path Syntax Requirements** ⚠️ **MANDATORY**

**For ALL \input commands, use this exact format:**

```latex
% CORRECT (Overleaf Compatible):
\input{tables/table_name.tex}
\input{figures/figure_name.tex}

% INCORRECT (Will cause compilation errors):
\input{../tables/table_name}     % Wrong relative path
\input{~~../~~tables/table_name} % Invalid tilde characters
\input{tables/table_name}        % Missing .tex extension
```

**Path Rules for Overleaf Compatibility:**
1. **No parent directory references**: Never use `../` in paths
2. **Always include .tex extension**: Required for \input commands
3. **Use forward slashes**: Directory separator must be `/`
4. **No special characters**: Avoid tildes (~) or other special characters
5. **Relative to main document**: Paths relative to main .tex file location

### **4.3 Table Files Template** ⚠️ **UPDATED**

Table files in `/tables/` directory:

```latex
% File: tables/table_name.tex
% NO \usepackage statements - rely on header.tex

\begin{table}[h!]
\centering
\caption{Table Caption}
\label{tab:table_label}
\begin{tabular}{@{}lll@{}}
\toprule
\textbf{Column 1} & \textbf{Column 2} & \textbf{Column 3} \\
\midrule
Data Row 1 & Data & Data \\
Data Row 2 & Data & Data \\
\bottomrule
\end{tabular}
\end{table}
```

## **FILE TRANSFER AND INTEGRATION PROTOCOL**

### **Step 1: Pre-Transfer Validation**
```bash
# Verify final directory structure
ls -la /mnt/d/immo_tool/final/

# Check main template compilation
cd /mnt/d/immo_tool/final/
pdflatex ht_eit_latex_template.tex
```

### **Step 2: File Compatibility Preparation** ⚠️ **MANDATORY**

Before transferring ANY files from `/work/` to `/final/`:

1. **Remove Document Structure Elements:**
   ```bash
   # Remove from ALL section files:
   - \documentclass declarations
   - \usepackage statements
   - \begin{document} and \end{document}
   - \maketitle, \tableofcontents, etc.
   ```

2. **Convert Bibliography:**
   ```bash
   # Convert manual bibliography to .bib entries
   # Add to /final/literature/references.bib
   ```

3. **Update Cross-References:**
   ```bash
   # Ensure all \ref{} and \label{} work with report class
   # Check figure/table numbering compatibility
   ```

### **Step 3: Systematic File Transfer**

```bash
# Transfer section files (after compatibility fixes)
cp /mnt/d/immo_tool/work/sections/*.tex /mnt/d/immo_tool/final/sections/

# Transfer table files (after compatibility fixes)
cp /mnt/d/immo_tool/work/tables/*.tex /mnt/d/immo_tool/final/tables/

# Update main template to include new sections
```

### **Step 4: Integration Testing** ⚠️ **MANDATORY**

```bash
# Test compilation in final directory
cd /mnt/d/immo_tool/final/
pdflatex ht_eit_latex_template.tex
biber ht_eit_latex_template  # For bibliography
pdflatex ht_eit_latex_template.tex
pdflatex ht_eit_latex_template.tex

# Verify output quality
# Check all cross-references work
# Verify bibliography appears correctly
```

### **Step 5: Overleaf Validation**

1. **Upload entire `/final/` directory to Overleaf**
2. **Verify compilation in Overleaf environment**
3. **Test all features work correctly**
4. **Validate final PDF output**

## **CRITICAL COMPATIBILITY CHECKLIST**

### **Before File Transfer:** ✅ **MANDATORY CHECKS**

- [ ] Remove all `\documentclass{}` from section files
- [ ] Remove all `\usepackage{}` from section files
- [ ] Remove all `\begin{document}` and `\end{document}` from section files
- [ ] Convert bibliography to `.bib` format
- [ ] Update main template to use `\include{}` instead of `\input{}`
- [ ] **FIX ALL PATH SYNTAX**: Ensure all `\input{}` commands use correct Overleaf syntax
  - [ ] No `../` parent directory references
  - [ ] All `.tex` extensions included
  - [ ] No tilde (~) characters in paths
  - [ ] Forward slashes (/) for directory separators
- [ ] Verify all labels and references use appropriate prefixes
- [ ] Check table formatting uses `booktabs` style
- [ ] Ensure no conflicting package requirements

### **After Integration:** ✅ **VALIDATION REQUIRED**

- [ ] Final directory compiles without errors
- [ ] Bibliography generates correctly with biblatex
- [ ] All cross-references work properly
- [ ] Table and figure numbering follows report class conventions
- [ ] Section hierarchy displays correctly
- [ ] PDF output matches expected institutional formatting
- [ ] Overleaf upload and compilation successful

## **TROUBLESHOOTING COMMON INTEGRATION ISSUES**

### **Issue 1: Package Conflicts**
```latex
% Remove from section files - packages loaded in header.tex:
\usepackage{booktabs}      % Already in header.tex
\usepackage{hyperref}      % Already in header.tex
\usepackage{graphicx}      % Already in header.tex
```

### **Issue 2: Bibliography Not Appearing**
```bash
# Ensure bibliography processing:
cd /mnt/d/immo_tool/final/
pdflatex ht_eit_latex_template.tex
biber ht_eit_latex_template
pdflatex ht_eit_latex_template.tex
```

### **Issue 3: Section Numbering Issues**
```latex
% Report class uses different numbering - ensure compatibility
% Check that section hierarchy works with institutional format
```

### **Issue 4: Cross-Reference Failures**
```latex
% Verify label format compatibility:
\label{sec:section_name}    % Sections
\label{tab:table_name}      % Tables
\label{fig:figure_name}     # Figures
```

### **Issue 5: LaTeX Path Errors** ⚠️ **CRITICAL FOR OVERLEAF**

**Problem:** Invalid `\input{}` path syntax causing compilation failures in Overleaf.

**Common Error Patterns:**
```latex
% BROKEN - Will cause compilation errors:
\input{../tables/table_name}         % Wrong relative path
\input{~~../~~tables/table_name}     % Invalid tilde characters
\input{tables/table_name}            % Missing .tex extension
\input{..\tables\table_name}         % Wrong directory separator
```

**Solution - Correct Path Syntax:**
```latex
% CORRECT - Overleaf compatible:
\input{tables/table_name.tex}        % Proper relative path with extension
\input{figures/figure_name.tex}      % Always include .tex extension
\input{sections/section_name.tex}    % Use forward slashes
```

**Mandatory Path Validation Checklist:**
- [ ] No `../` parent directory references in any `\input{}` commands
- [ ] All `\input{}` commands include `.tex` file extension
- [ ] No tilde (~) or special characters in file paths
- [ ] All paths use forward slashes (`/`) as directory separators
- [ ] All referenced files actually exist at specified paths
- [ ] Paths are relative to main document location

**Auto-Fix Command:**
```bash
# Scan for problematic paths in final directory:
grep -r "\\input{.*\\.\\./\\|\\input{.*~\\|\\input{[^}]*}$" /mnt/d/immo_tool/final/

# All results should be empty for Overleaf compatibility
```

## **UPDATED SUCCESS CRITERIA**

✅ All .tex files compile without errors in `/final/` directory
✅ Files integrate seamlessly with institutional LaTeX template
✅ Bibliography works correctly with biblatex system
✅ Cross-references function properly with report document class
✅ Final output matches institutional formatting requirements
✅ Overleaf upload and compilation successful
✅ No package conflicts or compatibility issues
✅ Data is current (collected within last 30 days)
✅ Sources are properly documented in .bib format
✅ Content provides actionable market insights

## **WORKFLOW SUMMARY**

1. **Develop in `/work/`** → Research and content creation
2. **Prepare for `/final/`** → Remove incompatible elements
3. **Transfer to `/final/`** → Copy compatible files
4. **Test integration** → Verify compilation and output
5. **Upload to Overleaf** → Final validation and delivery

⚠️ **CRITICAL**: Never transfer files without compatibility preparation. Always test in `/final/` before Overleaf upload.