# Python Project Template (VS Code • Pytest • GitLens • Google Docstrings)

A clean, minimal, and fully reproducible Python project template designed for use with VS Code. Includes pytest, Google‑style docstrings, GitLens‑optimized structure, and a workspace file for instant setup.

## 📁 Project Structure

```plaintext
📁 my_project/
├── 📁 src/                          # Source code (importable modules)
│   └── 📁 bandcamp                   # Package directory --- RENAME THIS ---
│       ├── 📄 bandcamp.py            # Module file --- RENAME THIS ---
│       └── 📄 __init__.py           # Makes directory a package
├── 📁 tests/                        # Pytest test suite
│   └── 📄 test_bandcamp.py          # 
├── 📁 .vscode/                      # Editor settings (pytest, docstrings)
│   └── 📄 settings.json
├── 📄 pyproject.toml                # Project metadata + pytest config
├── 📄 .gitignore                    # Files not tracked by GitHub
├── 📄 bandcamp.code-workspace       #
└── 📄 README.md                     # This File

```




##

## 🧪 Running Tests

### VS Code
- Open the Testing panel (beaker icon)
- Click Run All Tests

### Terminal
pytest

Pytest is configured through `pyproject.toml`:

[tool.pytest.ini_options]
pythonpath = ["src"]

This ensures imports like `from src.example.example import add` work without extra path hacks.

## 📝 Example Code (Google Docstrings)

### src/example/example.py
def add(a: int, b: int) -> int:
    """Add two integers.

    Args:
        a (int): The first integer.
        b (int): The second integer.

    Returns:
        int: The sum of `a` and `b`.

    Raises:
        TypeError: If either argument is not an integer.
    """
    if not isinstance(a, int) or not isinstance(b, int):
        raise TypeError("Both arguments must be integers.")
    return a + b

## 🧪 Example Test

### tests/test_example.py
from src.example.example import add

def test_add():
    """Test that add() returns the correct sum."""
    assert add(2, 3) == 5

## ⚙️ VS Code Configuration

`.vscode/settings.json` enables:
- pytest
- GitLens line + file history
- Google‑style docstring generation
- Clean file tree (hides `__pycache__` and `.pyc` files)

The workspace file (`example.code-workspace`) also:
- Loads recommended extensions
- Applies consistent settings across machines
- Keeps the environment reproducible

## 🚀 Quick Reference

```

### Environment Variables (Optional)
Create a `.env` file at the project root for local development:
```bash
# .env
PYTHONPATH=src
```

This file can be loaded by your IDE or shell for consistent configuration.



## 🔧 Common Tasks

### Add a New Module to Your Package
```bash
# Create a new .py file in your package
touch src/your_package/my_module.py

# Create a test file for it
touch tests/test_my_module.py
```

### Add a New Dependency
```bash
# Install the package
pip install package_name

# Add it to pyproject.toml
# Edit the [project] dependencies section

# Reinstall with your changes
pip install .[dev]
```

### Run Tests with Coverage
```bash
# Install coverage (add to [project.optional-dependencies] first)
pip install coverage pytest-cov

# Run tests with coverage
pytest --cov=src --cov-report=html
```

## 🐛 Troubleshooting

### Imports like `from src.example.example import ...` fail
**Solution**: Ensure your pytest configuration in `pyproject.toml` has:
```toml
[tool.pytest.ini_options]
pythonpath = ["src"]
```

And run pytest from the project root directory.

### `.venv` folder is large / slowing down Git
**Solution**: Ensure `.venv/` is in your `.gitignore`:
```bash
# In .gitignore
.venv/
venv/
env/
```

`.venv/` should stay local and should not be committed as part of a project template.

### `python -m venv .venv` fails because files already exist or are in use
**Solution**: This usually means `.venv/` already exists or one of its files is locked.

```bash
# Use the existing environment
# Activate it instead of recreating it
```

If you want to recreate it:
1. Close terminals or tools that are using `.venv`
2. Delete `.venv/`
3. Run `python -m venv .venv` again

### Virtual environment not activating on Windows
**Solution**: If the activation script fails, try:
```powershell
# Allow script execution (one-time)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Then activate
.venv\Scripts\Activate.ps1
```

### Changes to pyproject.toml not taking effect
**Solution**: Reinstall the package in editable mode:
```bash
pip install -e .[dev]
```

## 📚 Additional Resources

- [Python Packaging Guide](https://packaging.python.org/)
- [pytest Documentation](https://docs.pytest.org/)
- [PEP 517 - Python packaging build backend specification](https://www.python.org/dev/peps/pep-0517/)
- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html)
- [VS Code Python Extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [[VS Code Python ExtensionModern Web Automation with Python and Selenium]](https://realpython.com/modern-web-automation-with-python-and-selenium/) 

## 📦 Dependencies

This template intentionally keeps dependencies minimal:

- Python (any modern version)
- pytest (installed via pip)
- VS Code extensions:
  - Python
  - Pylance
  - GitLens
  - Jupyter
  - autoDocstring

## 🎯 Purpose

Use this to learn to use Selenium and control webpages

## 📜 License

You may use, modify, or extend this template freely.