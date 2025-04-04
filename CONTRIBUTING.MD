# Contributing to guMCP

Thank you for your interest in contributing to guMCP! This document provides guidelines and instructions to help you get started with development.

## Project Overview

- `src/`: Contains the main source code
  - `auth/`: Authentication components
  - `servers/`: Server implementations
- `tests/`: Test suite for the project
- `scripts/`: Utility scripts

## Development Environment Setup

### Prerequisites

- Python 3.11
- Git

### Setting Up Your Development Environment

1. **Clone the repository**

```bash
git clone https://github.com/gumloop/guMCP.git
cd guMCP
```

2. **Create a virtual environment**

```bash
python -m venv venv
```

3. **Activate the virtual environment**

On macOS/Linux:

```bash
source venv/bin/activate
```

On Windows:

```bash
venv\Scripts\activate
```

4. **Install dependencies**

```bash
# Install main dependencies
pip install -r requirements.txt

# Install development dependencies
pip install -r requirements-dev.txt
```

5. **Set up environment variables**

Copy the example .env file and update it with your configuration:

```bash
cp .env.example .env  # If an example exists, otherwise create your own
```

## Development Workflow

### Code Style and Standards

This project follows these coding standards:

- PEP 8 for Python code style
- Type hints for all functions and methods
- Documentation using docstrings

We use several tools to enforce these standards:

- Black for code formatting
- Flake8 for linting
- MyPy for type checking

### Running Code Quality Tools

You can run the code quality tools with the following command from the root directory:

```bash
# Format code with Black
python scripts/format_code.py

# Run linters
python scripts/lint.py
```

## Testing

### Running Tests

Tests can be run from the root directory using:

```bash
# Run specific tests locally (stdio)
python tests/servers/test_runner.py --server=simple-tools-server
# Run specific tests locally (sse) -- you would need to have the sse server running, ex. by running ./start_remote_dev_server.sh from the root directory
python tests/servers/test_runner.py --server=simple-tools-server --remote
# Run tests on a specific hosted guMCP server (ex. Gumloop's MCP Server)
python tests/servers/test_runner.py --server=simple-tools-server --remote --endpoint=https://mcp.gumloop.com/gdrive/{user_id}%3A{api_key}
```

### Manually Using Testing Clients

For Sandbox environments, we also provide `tests/clients/LocalMCPTestClient.py` and `tests/clients/RemoteMCPTestClient.py`.

These are based on Anthropic's example clients that connect to the MCP server and run a chat loop with stdio and SSE respectively.

Note: You must have an `ANTHROPIC_API_KEY` in your `.env` file for this to work correctly

### Writing Tests

When adding new features, please ensure you:

1. Write tests for new functionality
2. Ensure all tests pass before submitting a PR
3. Use pytest fixtures where appropriate
4. Use descriptive test names that follow the pattern `test_<functionality>_<expected_behavior>`

- All servers should have a corresponding `tests.py` file testing all tools, resources, prompts, etc.

## Pull Request Process

1. **Fork the repository** and create your branch from `main`
2. **Make your changes** and ensure they follow the project's code style
3. **Add tests** for any new functionality
4. **Ensure all tests pass** by running the test suite
5. **Update documentation** as needed
6. **Submit a pull request** with a clear description of the changes and why they're needed

## Versioning

We follow [Semantic Versioning](https://semver.org/) for this project.

## License

By contributing to this project, you agree that your contributions will be licensed under the project's license.

## Communication

If you have questions or need help, you can:

- Open an issue in the GitHub repository
- Contact the project maintainers via email or other communication channels

Thank you for contributing to guMCP!
