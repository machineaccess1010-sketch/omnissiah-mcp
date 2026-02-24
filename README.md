# Omnissiah MCP Servers

MCP (Model Context Protocol) servers for AI tool ecosystem. Enables Claude, Kimi, and other AI assistants to control Blender, browsers, and system tools securely.

## 🎯 Purpose

This repository contains MCP servers that act as **USB-C for AI** — standardized interfaces connecting AI models to external tools.

| Server | Function | Status |
|--------|----------|--------|
| **Blender** | 3D modeling, rendering, procedural generation | Planned |
| **Browser** | Web scraping, SEO analysis, form automation | Planned |
| **System** | Safe shell commands, file operations | Planned |

## 🏗️ Architecture

```
AI Models (Kimi, Claude) → MCP Client → MCP Server → Tool
                                    ↓
                              Sandboxed, audited, validated
```

## 🔒 Security

- **Sandboxed execution** — Docker containers with minimal privileges
- **Input validation** — Pydantic schemas, strict type checking
- **Audit logging** — All operations logged and reviewable
- **Whitelist-only** — No arbitrary code execution

## 🚀 Quick Start

```bash
# Clone
git clone https://github.com/machineaccess1010-sketch/omnissiah-mcp.git
cd omnissiah-mcp

# Install dependencies
pip install -r requirements.txt

# Run Blender MCP server
python -m mcp.blender.server
```

## 📦 Installation

### Via pip (when published)
```bash
pip install omnissiah-mcp
```

### Development
```bash
git clone https://github.com/machineaccess1010-sketch/omnissiah-mcp.git
pip install -e ".[dev]"
```

## 🛠️ Tools Exposed

### Blender MCP
- `create_primitive(type, name, location)` — Create basic 3D shapes
- `apply_modifier(object, modifier_type)` — Add mesh modifiers
- `render_scene(output_path, resolution)` — Render to file
- `export_mesh(format, path)` — Export to various formats

### Browser MCP
- `navigate(url)` — Load webpage
- `screenshot(path)` — Capture page image
- `extract_data(selector)` — Scrape structured data
- `fill_form(fields)` — Automate form submission

### System MCP
- `execute_command(command, args)` — Safe shell execution (whitelist-only)
- `read_file(path)` — Read file contents
- `write_file(path, content)` — Write file contents
- `list_directory(path)` — List directory contents

## 🔧 Configuration

Create `~/.config/omnissiah/mcp.yaml`:

```yaml
servers:
  blender:
    enabled: true
    port: 8080
    sandbox: true
  
  browser:
    enabled: true
    headless: true
    user_agent: "Omnissiah-Bot/1.0"
  
  system:
    enabled: true
    allowed_commands: ["git", "ls", "cat", "grep"]
    forbidden_patterns: ["rm -rf", "sudo", ">/dev"]
```

## 🧪 Testing

```bash
# Run all tests
pytest

# Test specific server
pytest tests/test_blender_mcp.py

# Security tests
pytest tests/test_security.py -v
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-tool`)
3. Commit changes (`git commit -m 'Add amazing tool'`)
4. Push to branch (`git push origin feature/amazing-tool`)
5. Open a Pull Request

All contributions must pass:
- Security scan (`trivy`, `gitleaks`, `semgrep`)
- Unit tests (`pytest`)
- Type checking (`mypy`)
- Linting (`ruff`, `black`)

## 📜 License

MIT License — see [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

- [Model Context Protocol](https://modelcontextprotocol.io/) — Anthropic's open standard
- [Blender Python API](https://docs.blender.org/api/current/) — For 3D operations
- [Playwright](https://playwright.dev/) — For browser automation

---

**Part of the Omnissiah ecosystem** | [Tools](https://github.com/machineaccess1010-sketch/omnissiah-tools) | [Soul Chat](https://github.com/machineaccess1010-sketch/soul-chat)
