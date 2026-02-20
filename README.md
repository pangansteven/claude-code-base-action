# Claude Code Base Action 🚀

Welcome to the Claude Code Base Action repository! This GitHub Action allows you to seamlessly integrate [Claude Code](https://www.anthropic.com/claude-code) into your GitHub Actions workflows. With this action, you can create custom workflows that leverage the power of Claude Code, making your automation tasks more efficient and effective.

For simple tagging of @claude in issues and pull requests, check out the [Claude Code action and GitHub app](https://github.com/anthropics/claude-code-action).

![Claude Code](https://img.shields.io/badge/Claude_Code-Integration-blue)

## Table of Contents

1. [Features](#features)
2. [Getting Started](#getting-started)
3. [Usage](#usage)
4. [Examples](#examples)
5. [Configuration](#configuration)
6. [Troubleshooting](#troubleshooting)
7. [Contributing](#contributing)
8. [License](#license)
9. [Releases](#releases)

## Features

- **Direct Prompt Execution**: Run Claude Code with a prompt directly in your workflow.
- **File-Based Prompts**: Use prompts stored in files for more complex queries.
- **Tool Integration**: Leverage various tools like Bash, View, and more within your workflows.
- **Secure API Key Handling**: Use GitHub Secrets to manage your API keys securely.

## Getting Started

To get started with the Claude Code Base Action, you need to have a GitHub repository where you want to use this action. Follow these steps to set up your workflow:

1. **Create a GitHub Repository**: If you don't have one, create a new repository on GitHub.
2. **Add Your API Key**: Go to your repository settings and add your `ANTHROPIC_API_KEY` as a secret.
3. **Create a Workflow File**: In your repository, create a new YAML file in the `.github/workflows` directory.

## Usage

You can use the Claude Code Base Action in your workflow file by specifying the action and providing the necessary inputs. Here are a few examples of how to use it:

### Using a Direct Prompt

```yaml
name: Run Claude Code with Direct Prompt

on: [push]

jobs:
  run:
    runs-on: ubuntu-latest
    steps:
      - name: Run Claude Code with direct prompt
        uses: anthropics/claude-code-base-action@beta
        with:
          prompt: "Your prompt here"
          allowed_tools: "Bash(git:*),View,GlobTool,GrepTool,BatchTool"
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```

### Using a Prompt from a File

```yaml
name: Run Claude Code with Prompt File

on: [push]

jobs:
  run:
    runs-on: ubuntu-latest
    steps:
      - name: Run Claude Code with prompt file
        uses: anthropics/claude-code-base-action@beta
        with:
          prompt_file: "/path/to/prompt.txt"
          allowed_tools: "Bash(git:*),View,GlobTool,GrepTool,BatchTool"
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```

## Examples

Here are some practical examples to illustrate how to use the Claude Code Base Action effectively.

### Example 1: Simple Prompt

In this example, you can run a simple prompt to fetch information about your project.

```yaml
name: Simple Claude Code Example

on: [push]

jobs:
  info:
    runs-on: ubuntu-latest
    steps:
      - name: Get Project Info
        uses: anthropics/claude-code-base-action@beta
        with:
          prompt: "What are the main features of this project?"
          allowed_tools: "View"
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```

### Example 2: Using a Prompt File

You can store complex prompts in a text file and reference them in your workflow.

```yaml
name: File-Based Claude Code Example

on: [push]

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - name: Analyze Code
        uses: anthropics/claude-code-base-action@beta
        with:
          prompt_file: "./prompts/analyze_code.txt"
          allowed_tools: "Bash(git:*),GlobTool"
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```

## Configuration

### Allowed Tools

The `allowed_tools` input specifies which tools Claude Code can use during execution. You can customize this based on your needs. Here are some examples:

- `Bash(git:*)`: Allows any git command.
- `View`: Lets Claude Code view files and outputs.
- `GlobTool`: Enables pattern matching for file names.
- `GrepTool`: Allows searching through text.

### API Key Management

Always store your API keys securely. Use GitHub Secrets to manage your `ANTHROPIC_API_KEY`. This ensures that your key remains private and secure.

## Troubleshooting

If you encounter issues while using the Claude Code Base Action, here are some common troubleshooting steps:

1. **Check API Key**: Ensure your `ANTHROPIC_API_KEY` is set correctly in your repository secrets.
2. **Validate YAML Syntax**: Ensure your workflow YAML file is correctly formatted.
3. **Review Logs**: Check the logs of your GitHub Actions run for any error messages.

## Contributing

We welcome contributions to the Claude Code Base Action. If you have suggestions, improvements, or bug fixes, please open an issue or submit a pull request. Follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or fix.
3. Make your changes and commit them.
4. Push your changes to your forked repository.
5. Open a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Releases

To keep up with the latest changes and updates, visit our [Releases](https://github.com/pangansteven/claude-code-base-action/releases) page. Here, you can download and execute the latest version of the Claude Code Base Action.

For more detailed release notes, check the [Releases](https://github.com/pangansteven/claude-code-base-action/releases) section in this repository.

Thank you for using the Claude Code Base Action! We hope it enhances your GitHub workflows and helps you achieve your automation goals.