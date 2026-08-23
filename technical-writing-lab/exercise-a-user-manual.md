# Exercise A — User Manual Procedure

## Creating and Activating a Python Virtual Environment and Installing a Package

### Prerequisites

Before beginning, make sure you have:

* A computer with Python 3 installed.
* A terminal or command prompt.
* Internet access.
* Basic knowledge of opening and using a terminal.
* Permission to create files and folders in your chosen project location.

## Procedure

### Step 1 — Create the project directory

Run the following command:

```bash
mkdir python_setup_lab
```

**Expected result:** A new directory named `python_setup_lab` is created.

### Step 2 — Open the project directory

Run:

```bash
cd python_setup_lab
```

**Expected result:** The terminal location changes to the `python_setup_lab` directory.

### Step 3 — Create the virtual environment

Run:

```bash
python3 -m venv venv
```

**Expected result:** A new directory named `venv` is created inside `python_setup_lab`.

### Step 4 — Activate the virtual environment

On Linux or macOS, run:

```bash
source venv/bin/activate
```

**Expected result:** `(venv)` appears at the beginning of the terminal prompt.

### Step 5 — Install the requests package

Run:

```bash
pip install requests
```

**Expected result:** Python downloads and installs the `requests` package and its required dependencies.

### Step 6 — Verify the package

Run:

```bash
pip show requests
```

**Expected result:** The terminal displays information about the installed `requests` package, including its version and installation location.

### Step 7 — Export the environment dependencies

Run:

```bash
pip freeze > requirements.txt
```

**Expected result:** A `requirements.txt` file is created containing the installed packages and their versions.

### Screenshot Description

A screenshot should show the terminal inside the `python_setup_lab` directory with `(venv)` visible in the terminal prompt. It should also show the `pip show requests` command and its output, including the installed package version and location. This demonstrates that the virtual environment is active and that the package was successfully installed.

### Troubleshooting

**Common error: `python3: command not found`**

This error means Python 3 is either not installed or is not available through the system PATH.

Run:

```bash
python3 --version
```

If the command still cannot be found, install Python 3 using the appropriate package manager for the operating system. After installation, run the virtual-environment creation command again.
