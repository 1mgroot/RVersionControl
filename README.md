# QuartoPaper Project

This project demonstrates reproducible research using Quarto with both R and Python. It uses `renv` for R package management and a Python virtual environment for Python dependencies.

## Quick Start

1. **Prerequisites**:
   - Install R (version 4.4.2 or later)
   - Install Python (version 3.11 or later)
   - Install RStudio (recommended)
   - Install Quarto

2. **Clone and Setup**:
   ```bash
   git clone [repository-url]
   cd QuartoPaper
   ```

3. **Initial Environment Setup**:
   - Open the project in RStudio
   - Render `renvSetup.qmd`:
     ```r
     quarto render renvSetup.qmd
     ```
   This will:
     - Initialize renv for R package management
     - Create Python virtual environment
     - Install all required packages
     - Generate documentation of all dependencies
   - Check `_output/renvSetup.html` for setup details and verification

4. **For Other Users (Environment Restoration)**:
   - Clone the repository
   - Open the project in RStudio
   - Render `restoreRenv.qmd`:
     ```r
     quarto render restoreRenv.qmd
     ```
   - Check `_output/restoreRenv.html` for environment status

## Project Structure

### Key Files
- `renvSetup.qmd` - Initial environment setup script
- `restoreRenv.qmd` - Environment restoration for other users
- `my-document.qmd` - Example document showing R and Python integration

### Configuration Files
- `_quarto.yml` - Quarto project configuration
- `renv.lock` - R package version lock file
- `requirements.txt` - Python package dependencies
- `python-config.json` - Python environment configuration
- `.Rprofile` - R environment settings

### Output Directory
- `_output/` - Contains rendered HTML files
  - `renvSetup.html` - Setup documentation
  - `restoreRenv.html` - Restoration documentation

### Environment Management
- `renv/` - R package management
  - Contains isolated R packages
  - Managed by renv
- `renv/python/` - Python virtual environment
  - Contains isolated Python packages
  - Managed through reticulate

## Working with the Environment

### R Packages
- Add new R packages:
  ```r
  renv::install("package_name")
  renv::snapshot()  # Update renv.lock
  ```

### Python Packages
- Add new Python packages:
  ```bash
  source renv/python/bin/activate
  pip install package_name
  pip freeze > requirements.txt  # Update requirements.txt
  ```

### Checking Dependencies
- View detailed dependency information:
  ```r
  quarto render renvSetup.qmd  # For current state
  ```
  or
  ```r
  quarto render restoreRenv.qmd  # For verification
  ```

## Troubleshooting

1. If R packages are missing:
   ```r
   renv::restore()
   ```

2. If Python packages are missing:
   ```r
   reticulate::virtualenv_install("renv/python", packages = readLines("requirements.txt"))
   ```

3. To completely reset the environment:
   - Delete `renv/python/` and `renv/library/`
   - Re-render `renvSetup.qmd`

## Notes
- The project uses renv to ensure reproducible R package versions
- Python dependencies are managed in an isolated virtual environment
- All configuration files are version controlled
- Environment setup and restoration processes are documented in Quarto files
- Output files are stored in `_output/` directory
- Code blocks in rendered HTML are collapsed by default but can be expanded 