# Playwright Automation Extension

This extension equips the agent with the ability to perform end-to-end (E2E) browser automation and testing using **Playwright**.

## Capabilities
- **Initialization**: Setup Playwright in new projects.
- **Test Generation**: Analyze source code and generate robust tests.
- **Execution**: Run tests and analyze failures.
- **Debugging**: Use UI mode and reports.

## Core Principles for the Agent
- **Robustness**: Always prioritize user-visible locators (Role, Text, Label) over implementation details (CSS classes).
- **Self-Correction**: If a test fails, analyze the error and offer to fix the code.
- **Safety**: Do not commit secrets/passwords in test files. Use environment variables.