# QuartoPaper Project

This project uses `renv` for R package management and a Python virtual environment for Python dependencies.

## Setup Instructions

1. **Prerequisites**:
   - Install R (version 4.4.2 or later)
   - Install Python (version 3.11 or later)
   - Install RStudio (recommended)
   - Install Quarto

2. **Clone the Repository**:
   ```bash
   git clone [repository-url]
   cd QuartoPaper
   ```

3. **Initialize R Environment**:
   - Open the project in RStudio by clicking on `QuartoPaper.Rproj`
   - The `.Rprofile` will automatically activate renv
   - When prompted, run:
     ```r
     renv::restore()
     ```
   This will install all required R packages in an isolated environment.

4. **Initialize Python Environment**:
   - The Python virtual environment will be automatically created in `renv/python`
   - All required Python packages are listed in `requirements.txt`
   - The environment is configured in `_quarto.yml` and `.Rprofile`

5. **Verify Setup**:
   In RStudio's R console, run:
   ```r
   reticulate::py_config()  # Should show Python path as renv/python/bin/python
   ```

6. **Render Documents**:
   - Open `my-document.qmd` in RStudio
   - Click the "Render" button or run:
     ```r
     quarto::quarto_render("my-document.qmd")
     ```

## Package Versions

### R Packages
To see R package versions, you have several options:

1. View direct dependencies (packages explicitly used in your code):
   ```r
   renv::dependencies()  # Shows only packages directly called in source files
   ```

2. View ALL dependencies (including indirect ones):
   ```r
   installed.packages()  # Shows all installed packages
   jsonlite::read_json("renv.lock")  # Shows complete dependency tree
   ```

   The `renv.lock` file contains all package information, including:
   - Direct dependencies (packages you use explicitly)
   - Indirect dependencies (packages required by other packages)
   - System requirements and versions

Key R packages in this project:
Direct dependencies:
- renv: 1.0.11
- rmarkdown: latest from CRAN

Indirect dependencies (loaded by Quarto/RStudio):
- R version: 4.4.2
- knitr: 1.49 (used by Quarto for document rendering)
- reticulate: 1.40.0 (used by Quarto for Python integration)

### Python Packages
To check Python package versions:
```bash
source renv/python/bin/activate    # Activate the virtual environment
pip freeze                        # List all installed packages and versions
```
The Python package requirements are listed in `requirements.txt`.

## Project Structure
- `renv/` - R package management
- `renv/python/` - Python virtual environment
- `requirements.txt` - Python package dependencies
- `_quarto.yml` - Quarto configuration
- `.Rprofile` - R environment configuration
- `renv.lock` - R package version lock file

## Notes
- The project uses renv to ensure reproducible R package versions
- Python dependencies are managed in an isolated virtual environment
- All necessary configuration files are version controlled 