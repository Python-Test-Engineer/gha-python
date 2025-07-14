# Set up

With a blank folder and just `.vscode` in it, run: `uv init`

This gives: 

![uv-init](./_images/01-uv-init.png)

It will have a `.python-version` file with current system Python version.

You can use `uv` to run Python projects with different Python versions. Here's how:

## 1. Run with a specific Python version directly

```bash
# Run with Python 3.9
uv run --python 3.9 your_script.py

# Run with Python 3.11
uv run --python 3.11 your_script.py

# Run with exact version
uv run --python 3.9.18 your_script.py
```

## 2. Create a virtual environment with specific Python version

If you don't create it specifically, one will be created `.venv` folder. This is also created with `uv venv`.

```bash
# Create venv with Python 3.9
uv venv --python 3.9

# Activate it
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
uv pip install -r requirements.txt

# Run your project
python your_script.py
```

## 3. Use uv sync with specific Python version

If you have a `pyproject.toml` file:

```bash
# Sync dependencies with Python 3.9
uv sync --python 3.9

# Then run
uv run your_script.py
```

## 4. Install Python version if needed

```bash
# uv can install Python versions for you
uv python install 311

# Then use it
uv run --python 3.11 src/calculator/calculator.py
```

Ensure `pyproject.toml` has suitable `requires-python = ">=3.11"` etc...

## 5. Set Python version in pyproject.toml

Add to your `pyproject.toml`:
```toml
[tool.uv]
python = "3.9"
```

Then simply run:
```bash
uv run your_script.py
```

The `--python` flag is the quickest way to specify a different Python version with uv. It will automatically download the Python version if it's not available on your system.

## Copy files

Copy over `src` and `tests` folders.

If you are using a different Python version in the `pyproject.toml` to that in `.python-version` then change the `.python-version` file to match the one in `pyproject.toml`.

`.\src\calculator\calculator.py` runs the script.

![run src](./_images/02-run-src.png)

# Sync

`uv sync` will sync your dependencies to the latest versions. It will also sync the Python version if needed.

`uv add --dev pytest` will add pytest to your project as a dev dependency.

`uv add pandas` will add pandas to your project as a regular dependency.

# Run tests

`uv run pytest -vs` will run pytest with verbose output.

![tests](./_images/03-pytest.png)


# Change Python version

`uv python pin 3.12` will pin your Python version to 3.12.

You can change in `pyproject.toml` if you want to change project.

# Remove existing venv
delete `.venv` folder

# Create new venv with different Python version
uv venv --python 3.12

# Reinstall dependencies
uv sync

# List PyPi packages

`uv python list  | Select-String "3\."` (windows)