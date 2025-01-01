# Quarto Paper Project

A template for reproducible research papers using Quarto with R and Python integration.

## Project Structure

- `renvSetup.qmd` - Snapshots current R and Python environments
- `restoreRenv.qmd` - Restores project environment on a new machine
- `my-document.qmd` - Example document with R and Python code
- `dependencies-info.qmd` - Displays detailed package information

## Prerequisites

- R (>= 4.2.0)
- Python (>= 3.11)
- Quarto (>= 1.3.0)

## Getting Started

### First Time Setup

If you're setting up this project for development:

1. Clone the repository
2. Open the project in RStudio
3. Run `renvSetup.qmd` to snapshot your environment

### Restoring Environment

If you're using an existing project:

1. Clone the repository
2. Open the project in RStudio
3. Run `restoreRenv.qmd` to restore the environment

## Environment Management

This project uses:
- `renv` for R package management
- Python virtual environment for Python package management
- Integrated R-Python environment through `reticulate`

## Contributing

1. Make your changes
2. Install any new packages needed
3. Run `renvSetup.qmd` to update environment snapshots
4. Commit all changes including:
   - `renv.lock`
   - `requirements.txt`
   - `python-config.json`

## License

This project is licensed under the MIT License - see the LICENSE file for details. 