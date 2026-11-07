# fraud_detection_analysis
# Reproducing the Project
<details> <summary><strong>Detailed Instructions</strong></summary>

<br>

The following instructions explain how to clone the repository, create the Python environment, select the correct Jupyter kernel, run the preprocessing scripts, and open the analysis notebooks.

## Prerequisites
Before beginning, make sure the following programs are installed:
- Git
- Python
- uv
- Visual Studio Code with the Python and Jupyter extensions, or JupyterLab

To confirm that Git and uv are installed, open a terminal and run:

```bash
git --version
uv --version
```

If both commands return version numbers, the required tools are available.

## 1. Clone the Repository

Open PowerShell, Windows Terminal, or another terminal and navigate to the folder where you want to store the project.

Clone the GitHub repository:

git clone https://github.com/abeaderstadt/fraud_detection_analysis

Move into the project directory:

cd fraud_detection_analysis

## 2. Create the Python Environment

This project uses uv to manage Python and project dependencies.

Install the required Python version listed in the project configuration:

```bash
uv python install
```

Create the virtual environment and install all project dependencies:

```bash
uv sync
```

This command creates a local .venv folder and installs the packages listed in pyproject.toml and uv.lock.

To confirm that the environment was created successfully, run:
```bash
uv run python --version
```

You can also confirm that the required packages are installed by running:

```bash
uv pip list
```

## 3. Open the Project in Visual Studio Code

From the project directory, launch Visual Studio Code:

code .

If the code command is unavailable, open Visual Studio Code manually and select:

File → Open Folder

Then choose the fraud_detection_analysis folder.

## 4. Select the Python Interpreter

In Visual Studio Code:

Open the Command Palette by pressing Ctrl+Shift+P.
Search for:
Python: Select Interpreter
Select the Python interpreter located inside the project's .venv folder.

On Windows, it will usually look similar to:

.venv\Scripts\python.exe

After selecting the interpreter, Visual Studio Code should use the project's virtual environment when running Python files.

## 5. Select the Jupyter Kernel

Open one of the notebooks in the notebooks folder:

notebooks/fraud_analysis.ipynb

or:

notebooks/

In the upper-right corner of the notebook, click Select Kernel.

Choose:

Python Environments

Then select the interpreter from the project's `.venv` folder.

On Windows, the selected kernel should point to something similar to:

.venv\Scripts\python.exe

If the environment does not appear in the kernel list:

1. Open the Command Palette with `Ctrl+Shift+P`.
2. Select:
Developer: Reload Window
1. Reopen the notebook and select the kernel again.

You can verify that the correct kernel is active by running the following code in a notebook cell:

import sys

print(sys.executable)

The output should include the project directory and `.venv`.

## 6. Confirm the Data Files

The repository contains separate folders for raw and processed data:

data/
├── raw/
└── processed/

The preprocessing script reads the original paysim dataset from data/raw/ and save cleaned datasets to data/processed/.

Before running the preprocessing workflow, confirm that the required raw CSV files are present in the data/raw/ folder.

## 7. Run the Data-Processing Scripts

The raw dataset is included in the `data/raw/` directory. To recreate the processed datasets used in the analysis, run the preprocessing script from the project root:

```bash
uv run python src/analysis.py
```

The script will clean and transform the raw file and save the resulting datasets to:

data/processed/

After running the script, review the terminal output for validation messages, dataset dimensions, missing-value summaries, or errors.


## 9. Run the Notebook

To reproduce all notebook outputs, select:

Run → Run All Cells

Run the notebooks in the following order:

1. notebooks/fraud_analysis.ipynb

Make sure the project's .venv kernel remains selected before running the cells.

The notebooks read the cleaned datasets from:

data/processed/

Some notebook cells may save charts or other visual outputs to:

figures/

## 10. Run Jupyter Notebook from Visual Studio Code

The notebooks can also be run directly inside Visual Studio Code.

After opening a notebook and selecting the `.venv` kernel:

1. Click Run All near the top of the notebook.
2. Allow each cell to finish before reviewing the output.
3. Confirm that no cells display errors.
4. Save the notebook after the outputs have been generated.

The kernel name shown in the upper-right corner should correspond to the project's `.venv` environment.


## Troubleshooting
The uv command is not recognized

Install uv, close the terminal, open a new terminal, and run:

uv --version
The virtual environment does not appear in Visual Studio Code

Run:

uv sync

Then reload Visual Studio Code:

Ctrl+Shift+P → Developer: Reload Window

After reloading, select the interpreter again.

The notebook cannot find a package

Confirm that the correct kernel is selected and run:

uv sync

Then restart the notebook kernel.

The notebook cannot find a data file

Make sure the notebook is being run from the cloned repository and that the required files exist in:

data/raw/

and:

data/processed/

Run the preprocessing scripts before running the notebooks.

File paths fail when running a script

Run all commands from the repository root:

cd fraud_detection_analysis

Then run the script using its full relative path:

uv run python src/data_processing/<script_name>.py

## Command Summary
git clone https://github.com/abeaderstadt/fraud_detection_analysis
cd fraud_detection_analysis

uv python install
uv sync

uv run python src/analysis.py

