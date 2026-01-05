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

## Troubleshooting Strategies

### 1. Handling "Hanging" CLI / Timeout Issues
- **Background Execution**: When tests might take a long time or block the CLI, use `nohup ... > output.log 2>&1 &` to run them in the background. Then, use `tail` or `cat` to inspect the logs.
- **Reporter Selection**: Use `--reporter=line` or `--reporter=list` to reduce verbose output that can clog the CLI buffer.
- **Health Checks**: Before running tests, verify dependencies (e.g., backend servers) are active using `lsof -i :<port>` or `curl`.
- **Debug Specs**: Create small, focused `debug.spec.ts` files that simply log page titles, URL, or HTML content to verify basic connectivity and rendering state.

### 2. Locator Best Practices (Ant Design & Chinese UI)
- **Text Spacing**: Ant Design buttons (and some other UI libraries) often insert spaces between Chinese characters (e.g., "登录" becomes "登 录").
  - **Solution**: Use regex with flexible whitespace: `.getByRole('button', { name: /登\s*录/ })`.
- **Select/Dropdowns**: Ant Design Select components can be tricky.
  - **Solution**: Prefer `.getByLabel('Label Text')` if available. If not, target the underlying input using `page.getByPlaceholder('...')` or `.locator('.ant-select-selection-search-input')` and `fill()` + `press('Enter')` instead of clicking options if the dropdown animation is flaky.
- **Waits**: Avoid hard `waitForTimeout`. Use assertions with timeouts (e.g., `await expect(locator).toBeVisible({ timeout: 10000 })`) to allow for dynamic loading times.