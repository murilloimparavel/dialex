# Contributing to Dialex

Thank you for your interest in contributing to Dialex! This project is in early development and we welcome contributions of all kinds.

## How to Contribute

### Reporting Issues
- Use [GitHub Issues](https://github.com/murilloimparavel/dialex/issues) to report bugs or suggest features
- Check existing issues before creating a new one
- Include as much context as possible

### Development Setup
```bash
# Clone the repository
git clone https://github.com/murilloimparavel/dialex.git
cd dialex

# Create a virtual environment
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
# .venv\Scripts\activate   # Windows

# Install dependencies
pip install -e ".[dev]"
```

### Pull Requests
1. Fork the repository
2. Create a feature branch: `git checkout -b feat/your-feature`
3. Make your changes
4. Run tests: `pytest`
5. Commit with conventional commits: `feat: add new feature`
6. Push and create a PR

### Commit Convention
We follow [Conventional Commits](https://www.conventionalcommits.org/):
- `feat:` — New feature
- `fix:` — Bug fix
- `docs:` — Documentation
- `refactor:` — Code refactoring
- `test:` — Tests
- `chore:` — Maintenance

### Code Style
- Python: Follow PEP 8, use type hints
- Use `ruff` for linting
- All new functions need docstrings

## Areas We Need Help

- [ ] Core debate engine implementation
- [ ] Knowledge graph storage layer (SQLite+JSON)
- [ ] CLI interface
- [ ] Multi-language documentation (ES, ZH)
- [ ] Testing and benchmarking
- [ ] Integrations with LLM providers

## Code of Conduct

Be respectful, constructive, and inclusive. We're building something that values productive disagreement — let's model that in our community.

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
