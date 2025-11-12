# Virtual Environments in Python

## Overview
Virtual environments create isolated Python environments for different projects, preventing dependency conflicts.

## Why Use Virtual Environments?

- **Isolation**: Each project has its own dependencies
- **Version Control**: Different projects can use different package versions
- **Clean System**: Keeps global Python installation clean
- **Reproducibility**: Easy to share project dependencies

## Creating Virtual Environments

### Using venv (Built-in)

```bash
# Create virtual environment
python -m venv myenv

# Or specify Python version
python3.9 -m venv myenv

# On Windows
python -m venv myenv

# On Linux/Mac
python3 -m venv myenv
```

### Activating Virtual Environment

```bash
# Windows
myenv\Scripts\activate

# Linux/Mac
source myenv/bin/activate

# Deactivate
deactivate
```

### Project Structure
```
myproject/
    myenv/          # Virtual environment
    src/            # Source code
    tests/          # Tests
    requirements.txt  # Dependencies
    README.md
```

## Managing Dependencies

### Installing Packages

```bash
# Install package
pip install requests

# Install specific version
pip install requests==2.28.0

# Install from requirements file
pip install -r requirements.txt

# Upgrade package
pip install --upgrade requests

# Uninstall package
pip uninstall requests
```

### requirements.txt

```bash
# Create requirements file
pip freeze > requirements.txt

# Example requirements.txt
requests==2.31.0
numpy>=1.24.0
pandas~=1.5.0
flask
pytest>=7.0.0
```

### Version Specifiers

```text
==  # Exact version
>=  # Minimum version
<=  # Maximum version
~=  # Compatible release
!=  # Exclude version
```

## Using virtualenv (Alternative)

```bash
# Install virtualenv
pip install virtualenv

# Create environment
virtualenv myenv

# Create with specific Python version
virtualenv -p python3.9 myenv

# Activate (same as venv)
source myenv/bin/activate  # Linux/Mac
myenv\Scripts\activate     # Windows
```

## pipenv (Modern Alternative)

```bash
# Install pipenv
pip install pipenv

# Create environment and install packages
pipenv install requests

# Install dev dependencies
pipenv install pytest --dev

# Activate environment
pipenv shell

# Run command in environment
pipenv run python script.py

# Generate requirements
pipenv lock -r > requirements.txt
```

## Best Practices

### 1. One Environment Per Project
```bash
# Each project gets its own environment
project1/
    venv/
    requirements.txt
project2/
    venv/
    requirements.txt
```

### 2. Never Commit venv Folder
```gitignore
# .gitignore
venv/
myenv/
__pycache__/
*.pyc
```

### 3. Document Dependencies
```text
# requirements.txt with comments
# Web framework
flask==2.3.0

# Database
sqlalchemy>=1.4.0

# Testing
pytest>=7.0.0
```

### 4. Separate Dev Dependencies
```text
# requirements.txt (production)
flask==2.3.0
requests==2.31.0

# requirements-dev.txt (development)
pytest>=7.0.0
black>=22.0.0
flake8>=4.0.0
```

## Common Commands

```bash
# List installed packages
pip list

# Show package info
pip show requests

# Check outdated packages
pip list --outdated

# Install from GitHub
pip install git+https://github.com/user/repo.git

# Install in editable mode
pip install -e .

# Create wheel file
pip wheel .
```

## Troubleshooting

### Can't Activate on Windows
```powershell
# Enable script execution
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Wrong Python Version
```bash
# Specify Python version explicitly
python3.9 -m venv myenv
```

### Corrupted Environment
```bash
# Delete and recreate
rm -rf myenv
python -m venv myenv
```

---

## Practice Questions

### Multiple Choice Questions

**1. What is a virtual environment?**
a) Isolated Python environment  
b) Cloud server  
c) IDE feature  
d) Package manager

**2. How to create virtual environment?**
a) `python -m venv myenv`  
b) `create venv myenv`  
c) `new venv myenv`  
d) `venv create myenv`

**3. What is requirements.txt?**
a) Project documentation  
b) List of dependencies  
c) Configuration file  
d) Test file

**4. Should venv folder be committed to git?**
a) Yes  
b) No  
c) Sometimes  
d) Depends

**5. How to activate venv on Windows?**
a) `venv\Scripts\activate`  
b) `source venv/bin/activate`  
c) `activate venv`  
d) `venv activate`

---

## Coding Exercises

**Exercise 1:** Create a virtual environment named "project_env".

**Exercise 2:** Create requirements.txt with requests, numpy, and pandas.

**Exercise 3:** Write script to check if running in virtual environment.

**Exercise 4:** Create .gitignore file for Python project.

---

## Answers

**Solution 1:**
```bash
# Create virtual environment
python -m venv project_env

# Activate
# Windows:
project_env\Scripts\activate
# Linux/Mac:
source project_env/bin/activate

# Verify
which python  # Linux/Mac
where python  # Windows
```

**Solution 2:**
```text
# requirements.txt
requests>=2.28.0
numpy>=1.24.0
pandas>=1.5.0

# Install all
pip install -r requirements.txt
```

**Solution 3:**
```python
import sys

def is_venv():
    """Check if running in virtual environment"""
    return (hasattr(sys, 'real_prefix') or
            (hasattr(sys, 'base_prefix') and sys.base_prefix != sys.prefix))

if is_venv():
    print("Running in virtual environment")
else:
    print("Running in system Python")
```

**Solution 4:**
```gitignore
# .gitignore for Python project

# Virtual environment
venv/
env/
ENV/
.venv

# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python

# Distribution
build/
dist/
*.egg-info/

# IDE
.vscode/
.idea/
*.swp

# Testing
.pytest_cache/
.coverage
htmlcov/

# Environment
.env
.env.local
```
