# github-repo-create

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

**github-repo-create** (ghrc.sh) is a Bash script designed to streamline the process of creating a new GitHub repository from the current local git project, pushing your code, and generating a professional `README.md` file using OpenAI’s API. It leverages the GitHub CLI (`gh`), `jq`, and automatically selects your main entrypoint file. The README is generated via a local prompt template and contents of your entrypoint file, ensuring the documentation is both accurate and project-specific.

**Note:** This readme was generated using this script!

---

## Features

- Creates a public GitHub repository from your current directory.
- Pushes local code and sets `origin` remote.
- Automatically generates `README.md` using OpenAI’s language model.
- Supports specifying a custom entrypoint file.
- Enforces environment and tool prerequisites for reliability.
- Commits and pushes the newly generated README.

---

## Prerequisites

The following tools and environment variables must be available in your CLI environment:

- **git** (repository should already be initialized)
- **gh** (GitHub CLI)  
  [Installation guide](https://cli.github.com/manual/installation)
- **jq** (JSON processor)  
  [Installation](https://stedolan.github.io/jq/download/)
- **curl** (for API requests)
- **OPENAI_API_KEY** environment variable must be exported with your OpenAI API key.
- **.ghrc-prompt** prompt template in your `$HOME` directory (for example: `/home/username/.ghrc-prompt`)
- *(Optional)* **OPENAI_MODEL** environment variable to specify the model (defaults to `gpt-4.1`)

---

## Installation

No special installation is required; simply clone the repository and use the main script.

### Clone the Repository

To get started, clone the project:

```bash
git clone https://github.com/ohnotnow/github-repo-create.git
cd github-repo-create
chmod +x ghrc.sh
```

---

## Usage

```bash
./ghrc.sh <repo-name> [entrypoint-file]
```

- `<repo-name>`: Name for the new GitHub repository (required).
- `[entrypoint-file]`: Main file of your project (optional; defaults to `main.py`).

**Examples:**
```bash
./ghrc.sh my-new-repo main.py
./ghrc.sh cool-utils app.js
```

### Process Flow

1. Confirms you're inside a git repository.
2. Checks specified entrypoint file exists.
3. Verifies required tools (`gh`, `jq`) are available.
4. Reads prompt template from `$HOME/.ghrc-prompt`.
5. Uses GitHub CLI to create and push the repo.
6. Calls OpenAI API to generate `README.md` and commits it.
7. Pushes the README addition to GitHub.

---

## Environment Variables

- **OPENAI_API_KEY**: Your OpenAI API key (required).
- **OPENAI_MODEL**: Language model for OpenAI API (optional, defaults to `gpt-4.1`).

Example for Unix shells:

```bash
export OPENAI_API_KEY='your-openai-key'
export OPENAI_MODEL='gpt-4o-mini'
```

---

## OS Compatibility

All CLI commands are cross-platform for MacOS, Ubuntu, and Windows (using Git Bash or WSL). Ensure the prerequisite tools are installed using the preferred package manager for your system:

- **MacOS (Homebrew):**
    ```bash
    brew install gh jq
    ```
- **Ubuntu (APT):**
    ```bash
    sudo apt update
    sudo apt install gh jq curl
    ```
- **Windows (Git Bash, Chocolatey, or winget):**
    ```bash
    choco install gh jq curl
    ```
    or
    ```
    winget install GitHub.cli
    winget install jq
    winget install curl
    ```

---

## License

This project is licensed under the [MIT License](LICENSE).

---

## Additional Notes

- The prompt template must be present at `${HOME}/.ghrc-prompt` for the script to generate meaningful documentation.
- Any errors or missing prerequisites will halt the script with clear error messages.
- For questions or improvements, please open an issue or submit a pull request.

---

## Repository

[github-repo-create on GitHub](https://github.com/ohnotnow/github-repo-create)
