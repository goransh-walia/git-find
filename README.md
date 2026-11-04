<div align="center">

# 🔍 git-find

**Find GitHub repositories, users and code straight from your terminal, and let your AI assistant do it too.**

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![MCP](https://img.shields.io/badge/MCP-server-8A2BE2)
![Status](https://img.shields.io/badge/status-active-brightgreen)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-orange)

</div>

---

## 📖 Table of Contents

- [About](#-about)
- [Features](#-features)
- [Demo](#-demo)
- [Requirements](#-requirements)
- [Installation](#-installation)
- [Usage](#-usage)
- [GitHub Token (optional)](#-github-token-optional)
- [MCP Server](#-mcp-server)
- [Project Structure](#-project-structure)
- [Troubleshooting](#-troubleshooting)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 📌 About

**git-find** is a lightweight Python tool for searching GitHub without leaving your terminal. It also includes an **MCP (Model Context Protocol) server**, so AI assistants such as Claude can search GitHub on your behalf.

No heavy setup, no browser tabs. Run a command, get results.

## ✨ Features

- 🔎 Search GitHub repositories, users and code from the command line
- 🎯 Filter results by language, stars, topic, etc. *(edit to match your script)*
- 🤖 Built-in MCP server (`gitfind_mcp.py`) for AI assistants
- 🔑 Optional GitHub token support for higher API rate limits
- 🪶 Lightweight and written in pure Python
- 💻 Works on Windows, macOS and Linux

## 🎬 Demo

```text
$ python gitfind.py "machine learning" --language python

1. user/awesome-ml        ⭐ 12.4k   Python   A curated list of ML resources
2. user/ml-from-scratch   ⭐  8.1k   Python   Machine learning algorithms in NumPy
3. user/ml-notes          ⭐  2.3k   Python   Study notes and examples
```

> 📸 Replace the block above with real output or a screenshot/GIF of your tool running.

## 📋 Requirements

- Python **3.9 or newer**
- `pip` (comes with Python)
- Internet connection
- *(Optional)* A GitHub Personal Access Token

## 🚀 Installation

```bash
# 1. Clone the repository
git clone https://github.com/goransh-walia/git-find.git
cd git-find

# 2. (Recommended) create a virtual environment
python -m venv venv

# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt
```

## 🧭 Usage

Basic search:

```bash
python gitfind.py "your search query"
```

Examples:

```bash
# Search repositories
python gitfind.py "web scraper"

# Filter by language
python gitfind.py "web scraper" --language python

# See all options
python gitfind.py --help
```

> Update the commands and flags above so they match your script.

## 🔑 GitHub Token (optional)

Without a token, GitHub limits how many API requests you can make. A token raises that limit.

1. Go to **GitHub → Settings → Developer settings → Personal access tokens**
2. Generate a token (no special scopes are needed for public searches)
3. Set it as an environment variable:

```bash
# Windows (Command Prompt)
set GITHUB_TOKEN=your_token_here

# macOS / Linux
export GITHUB_TOKEN=your_token_here
```

> ⚠️ **Never commit your token.** Keep it in an environment variable or a `.env` file, and make sure `.env` is listed in `.gitignore`.

## 🤖 MCP Server

`gitfind_mcp.py` exposes git-find as an [MCP](https://modelcontextprotocol.io) server, so AI assistants can call it as a tool.

Run it directly to test:

```bash
python gitfind_mcp.py
```

Add it to your MCP client config (for example, Claude Desktop's `claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "gitfind": {
      "command": "python",
      "args": ["C:/full/path/to/git-find/gitfind_mcp.py"],
      "env": {
        "GITHUB_TOKEN": "your_token_here"
      }
    }
  }
}
```

Restart your MCP client, and the assistant can now search GitHub through git-find.

## 📁 Project Structure

```text
git-find/
├── gitfind.py          # Command-line search tool
├── gitfind_mcp.py      # MCP server for AI assistants
├── requirements.txt    # Python dependencies
├── .gitignore          # Files Git should ignore
├── LICENSE             # MIT license
└── README.md           # You are here
```

## 🛠 Troubleshooting

| Problem | Fix |
|---|---|
| `python` is not recognized | Reinstall Python and tick **Add Python to PATH**, or try `py` instead of `python` |
| `ModuleNotFoundError` | Run `pip install -r requirements.txt` inside your virtual environment |
| `403 rate limit exceeded` | Set a `GITHUB_TOKEN` (see above) or wait a few minutes |
| MCP server not showing up | Use the **full absolute path** in the config and restart the client |

## 🗺 Roadmap

- [ ] Pretty-printed output with colors
- [ ] Export results to JSON / CSV
- [ ] Search issues and pull requests
- [ ] Caching to reduce API calls
- [ ] Publish to PyPI (`pip install git-find`)
- [ ] Unit tests and GitHub Actions CI

## 🤝 Contributing

Contributions, issues and feature requests are welcome!

1. Fork the repo
2. Create your branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m "Add my feature"`
4. Push the branch: `git push origin feature/my-feature`
5. Open a Pull Request

## 📄 License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for details.

## 👤 Author

**Goransh Walia**

- GitHub: [@goransh-walia](https://github.com/goransh-walia)
- LinkedIn: [goransh-walia](https://www.linkedin.com/in/goransh-walia-85065b383/)

---

<div align="center">

If you find this useful, drop a ⭐ on the repo!

</div>
