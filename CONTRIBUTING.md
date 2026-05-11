# Contributing to OpenAPI Collection Generator

Thank you for your interest in contributing! This document outlines how to get involved and the conventions we follow.

## Ways to Contribute

- Report bugs and unexpected behavior
- Suggest new features or improvements
- Improve documentation
- Submit pull requests with bug fixes or new functionality

## Reporting Issues

Before opening an issue, please:

1. Search [existing issues](../../issues) to avoid duplicates.
2. Use a clear, descriptive title.
3. Include:
   - A minimal reproduction (OpenAPI snippet, plugin configuration, command used)
   - Expected vs. actual behavior
   - Plugin version, Java version, Maven version, OS
   - Relevant logs or stack traces

## Development Setup

### Prerequisites

- Java 17+
- Maven 3.9+
- Git

### Build

```bash
git clone https://github.com/rspereiratech/openapi-collection-generator-parent.git
cd openapi-collection-generator-parent
mvn clean install
```

### Run Tests

```bash
mvn test
```

### Module Layout

| Module | Description |
|---|---|
| `openapi-collection-generator-parent` | Parent POM with shared dependency management |
| `openapi-collection-generator-core` | Core library with generation orchestration, parsing, and writing |
| `openapi-collection-generator-postman` | Postman collection generator |
| `openapi-collection-generator-insomnia` | Insomnia collection generator |
| `openapi-collection-generator-maven-plugin` | Maven plugin (thin wrapper over core) |

## Pull Request Process

1. **Fork** the repository and create your branch from `master`:
   ```bash
   git checkout -b feature/my-change
   ```
2. **Make your changes**, keeping commits focused and atomic.
3. **Add tests** for new functionality or bug fixes.
4. **Ensure the build passes**:
   ```bash
   mvn clean verify
   ```
5. **Update documentation** (README, configuration reference) when behavior changes.
6. **Open a pull request** with:
   - A clear description of the change and motivation
   - Reference to any related issue (`Closes #123`)
   - Notes on backwards compatibility, if applicable

### Commit Messages

- Use the imperative mood: "Add support for X", not "Added" or "Adds".
- Keep the subject line under 72 characters.
- Provide a longer body when the change benefits from explanation.

### Code Style

- Follow standard Java conventions and the existing code style.
- Prefer clear, self-documenting code over comments.
- Keep public APIs stable; flag breaking changes explicitly in the PR.

## Adding a New Output Format

To add support for a new collection format (e.g. Bruno, HTTPie):

1. Create a new module `openapi-collection-generator-<format>`.
2. Implement the generator interface defined in `openapi-collection-generator-core`.
3. Register the format in the plugin's `Format` enum.
4. Add unit tests covering representative OpenAPI specs.
5. Update the README and configuration reference.

## Code of Conduct

Be respectful and constructive. Disagreements should focus on technical merit. See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) for details.

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).
