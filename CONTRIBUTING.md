
# Contributing to Numblio

Thank you for considering contributing to Numblio! We welcome contributions from the community to help improve our project. Whether you're fixing a bug, adding a new feature, or improving documentation, your efforts are greatly appreciated.

## Table of Contents

- [Getting Started](#getting-started)
- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
  - [Reporting Issues](#reporting-issues)
  - [Suggesting Enhancements](#suggesting-enhancements)
  - [Submitting Changes](#submitting-changes)
- [Coding Standards](#coding-standards)
- [Commit Messages](#commit-messages)
- [Pull Request Process](#pull-request-process)
- [Community Support](#community-support)
- [License](#license)

---

## Getting Started

- **Fork the Repository**: Click on the "Fork" button at the top of the repository page to create a copy on your GitHub account.
- **Clone the Fork**: Clone your forked repository to your local machine.

  ```bash
  git clone https://github.com/numblio/repository.git
  ```

- **Set Upstream Remote**: Set the original repository as the upstream remote.

  ```bash
  cd repository
  git remote add upstream https://github.com/numblio/numblio.git
  ```

- **Install Dependencies**: Install the necessary dependencies as per the project's README.

## Code of Conduct

By participating in this project, you agree to abide by the [Numblio Code of Conduct](CODE_OF_CONDUCT.md). Please read it to understand the expectations for all contributors.

## How to Contribute

### Reporting Issues

If you encounter a bug or have a question, please check the [existing issues](https://github.com/numblio/numblio-documentation/issues) before creating a new one. When reporting a new issue, provide as much detail as possible:

- A clear and descriptive title.
- Steps to reproduce the issue.
- Expected and actual results.
- Screenshots or code snippets, if applicable.
- Your environment details (e.g., operating system, browser version).

### Suggesting Enhancements

We welcome suggestions for new features or improvements. Please open an issue with:

- A clear and descriptive title.
- A detailed explanation of the enhancement.
- Any relevant examples or use cases.

### Submitting Changes

Before starting work on a significant change, please open an issue to discuss your proposal. This helps prevent duplicate efforts and ensures your contribution aligns with the project's goals.

## Coding Standards

- **Style Guide**: Follow the coding conventions used in the project. Consistency helps maintain readability.

  - **Languages**: The project uses [PHP](https://www.php.net/) (Laravel framework) and [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript).
  - **PHP Standards**: Follow [PSR-12](https://www.php-fig.org/psr/psr-12/) coding style.
  - **JavaScript Standards**: Use [ESLint](https://eslint.org/) with the recommended settings.

- **Comments**: Write clear and concise comments where necessary.
- **Documentation**: Update the documentation if your changes affect it.

## Commit Messages

- **Format**: Use the following format for commit messages:

  ```
  Subject line (50 characters or less)

  Detailed description explaining the commit (if necessary).
  ```

- **Subject Line**: Should be concise and use the imperative mood (e.g., "Add feature" instead of "Added feature").
- **Reference Issues**: Include issue numbers if applicable (e.g., `Fixes #123`).

## Pull Request Process

1. **Sync with Upstream**: Ensure your fork is up-to-date with the upstream repository.

   ```bash
   git checkout main
   git fetch upstream
   git merge upstream/main
   ```

2. **Create a Feature Branch**: Use a descriptive name.

   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make Changes**: Implement your changes and commit them following the commit message guidelines.

4. **Push to Your Fork**:

   ```bash
   git push origin feature/your-feature-name
   ```

5. **Open a Pull Request**:

   - Go to your fork on GitHub.
   - Click on the "Compare & pull request" button.
   - Fill out the pull request template, providing a clear description of your changes.

6. **Review Process**:

   - Your pull request will be reviewed by project maintainers.
   - Be responsive to feedback and make necessary changes.
   - Once approved, your pull request will be merged.

## Community Support

If you need help or have questions, feel free to:

- Open an issue on GitHub.
- Contact us via email at [support@numblio.com](mailto:support@numblio.com).

## License

By contributing to Numblio, you agree that your contributions will be licensed under the [MIT License](LICENSE).

---

Thank you for your interest in contributing to Numblio!
