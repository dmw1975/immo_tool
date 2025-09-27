# Swiss Real Estate Market Research Tool

A comprehensive tool for Swiss real estate market analysis using web crawling, data collection, and LaTeX document generation for institutional academic reports.

## 📋 Overview

This repository contains an automated research tool that:
- Collects Swiss real estate market data from official sources
- Generates comprehensive LaTeX documents compatible with institutional templates
- Produces Overleaf-ready research reports with proper formatting
- Provides systematic data analysis and visualization

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Git
- LaTeX distribution (TeX Live recommended)
- Internet connection for data collection

### Repository Structure

```
immo_tool/
├── README.md              # This file
├── CLAUDE.md              # Complete project specification and instructions
├── requirements.txt       # Python dependencies
├── .gitignore            # Git ignore configuration
├── work/                 # Temporary working directory (gitignored)
├── final/                # Institutional template directory (gitignored)
└── .venv/                # Virtual environment (gitignored)
```

## 🖥️ Setup Instructions

### For WSL (Windows Subsystem for Linux) Users

#### 1. Enable WSL and Install Ubuntu
```bash
# Run in Windows PowerShell as Administrator
wsl --install
# Or install specific Ubuntu version
wsl --install -d Ubuntu-24.04
```

#### 2. Update System Packages
```bash
# Run in WSL terminal
sudo apt update && sudo apt upgrade -y
```

#### 3. Install Required System Dependencies
```bash
# Install Python and development tools
sudo apt install python3 python3-pip python3-venv git curl wget -y

# Install LaTeX (full installation for comprehensive support)
sudo apt install texlive-full -y

# Alternative minimal LaTeX installation (faster)
# sudo apt install texlive-latex-base texlive-latex-extra texlive-fonts-recommended texlive-bibtex-extra biber -y
```

#### 4. Clone and Setup Repository
```bash
# Navigate to your preferred directory (e.g., /mnt/d/ for D: drive access)
cd /mnt/d/

# Clone the repository
git clone https://github.com/YOUR_USERNAME/immo_tool.git
cd immo_tool

# Create and activate virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install Python dependencies
pip install -r requirements.txt
```

#### 5. WSL-Specific Configuration
```bash
# Configure git if not already done
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set up VS Code integration (optional)
code .  # Opens repository in VS Code with WSL extension
```

### For Mac Users

#### 1. Install Homebrew (if not already installed)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### 2. Install Required Dependencies
```bash
# Install Python and Git
brew install python git

# Install LaTeX (MacTeX - comprehensive)
brew install --cask mactex

# Alternative: BasicTeX (minimal installation)
# brew install --cask basictex
# sudo tlmgr update --self
# sudo tlmgr install collection-fontsrecommended collection-latexextra biber biblatex
```

#### 3. Clone and Setup Repository
```bash
# Navigate to your preferred directory
cd ~/Documents  # or preferred location

# Clone the repository
git clone https://github.com/YOUR_USERNAME/immo_tool.git
cd immo_tool

# Create and activate virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install Python dependencies
pip install -r requirements.txt
```

#### 4. Mac-Specific Configuration
```bash
# Configure git if not already done
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Add LaTeX to PATH (if using BasicTeX)
echo 'export PATH="/usr/local/texlive/2024/bin/universal-darwin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

## 📖 Usage Instructions

### 1. Read the Complete Specification
```bash
# Read CLAUDE.md for comprehensive project instructions
cat CLAUDE.md
```

### 2. Execute the Research Tool
The tool is designed to be executed by Claude Code following the instructions in `CLAUDE.md`. The main workflow involves:

1. **Data Collection Phase**: Automated web crawling and data gathering from Swiss official sources
2. **Processing Phase**: Data analysis and LaTeX document structure creation
3. **Generation Phase**: Complete research report generation in institutional template format

### 3. Key Commands

#### Activate Virtual Environment
```bash
# WSL and Mac
source .venv/bin/activate
```

#### Check LaTeX Installation
```bash
# Verify LaTeX installation
pdflatex --version
biber --version
```

#### Validate Generated Documents
```bash
# Check for path syntax issues (should return empty)
grep -r "\\input{.*\\.\\./\\|\\input{.*~\\|\\input{[^}]*}$" final/
```

## 🔧 Troubleshooting

### Common Issues and Solutions

#### WSL-Specific Issues

**1. Permission Issues**
```bash
# Fix file permissions
sudo chown -R $USER:$USER /mnt/d/immo_tool
chmod -R 755 /mnt/d/immo_tool
```

**2. LaTeX Path Issues**
```bash
# Update PATH for LaTeX
echo 'export PATH="/usr/local/texlive/2024/bin/x86_64-linux:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

**3. Network Issues in WSL**
```bash
# Reset WSL network
wsl --shutdown
# Restart WSL
```

#### Mac-Specific Issues

**1. MacTeX PATH Issues**
```bash
# Check if LaTeX is in PATH
which pdflatex

# If not found, add to PATH
echo 'export PATH="/Library/TeX/texbin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

**2. Homebrew Permission Issues**
```bash
# Fix Homebrew permissions
sudo chown -R $(whoami) $(brew --prefix)/*
```

#### General Issues

**1. Python Virtual Environment Issues**
```bash
# Recreate virtual environment
rm -rf .venv
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

**2. LaTeX Compilation Errors**
```bash
# Clear LaTeX cache
rm -f final/*.aux final/*.log final/*.bbl final/*.blg final/*.toc
```

**3. Git Issues**
```bash
# Reset git state if needed
git status
git add .
git commit -m "Update repository state"
```

## 📁 Directory Workflow

### Work Directory (`work/`)
- Temporary processing and development files
- Not tracked by git (in .gitignore)
- Safe for experimentation and intermediate files

### Final Directory (`final/`)
- Institutional template-compatible LaTeX files
- Overleaf-ready document structure
- Not tracked by git (in .gitignore)
- Generated output should be exported manually if needed

## 🔍 Validation Commands

### Pre-Execution Checklist
```bash
# 1. Check Python environment
python --version
pip list | grep -E "(requests|beautifulsoup4|pandas)"

# 2. Check LaTeX installation
pdflatex --version
biber --version

# 3. Check repository status
git status
ls -la
```

### Post-Execution Validation
```bash
# 1. Validate LaTeX paths (should be empty)
grep -r "\\input{.*\\.\\./\\|\\input{.*~\\|\\input{[^}]*}$" final/

# 2. Check file structure
find final/ -name "*.tex" | head -10

# 3. Test LaTeX compilation (if main file exists)
cd final/
pdflatex ht_eit_latex_template.tex
```

## 📚 Additional Resources

- **CLAUDE.md**: Complete project specification and execution instructions
- **Swiss Federal Statistical Office**: https://www.bfs.admin.ch/
- **Swiss National Bank**: https://www.snb.ch/
- **Overleaf Documentation**: https://www.overleaf.com/learn
- **LaTeX Documentation**: https://www.latex-project.org/help/documentation/

## 🤝 Contributing

This repository follows institutional academic standards. When making modifications:

1. Ensure LaTeX compatibility with Overleaf
2. Maintain proper path syntax (no `../`, include `.tex` extensions)
3. Follow the institutional template requirements in `final/`
4. Update documentation for any workflow changes

## ⚠️ Important Notes

- **Never commit** `.tex` files, virtual environments, or temporary data to git
- **Always validate** LaTeX path syntax before finalizing documents
- **Test compilation** on Overleaf before submitting institutional reports
- **Respect rate limits** when web crawling official Swiss government sites

## 📄 License

This tool is designed for academic research purposes. Ensure compliance with data source terms of service and institutional requirements.