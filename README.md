# Hello World VSCode Extension

A simple "Hello World" VSCode extension that demonstrates the basic structure and functionality of a VSCode extension.

## Features

This extension adds a "Hello World" command to VSCode that displays a greeting message.

- Command: `Hello World`
- Activation: Command Palette (Ctrl+Shift+P or Cmd+Shift+P)

## Requirements

- Visual Studio Code version 1.109.0 or higher
- Node.js 20.x or higher
- npm 9.x or higher

## Development Setup

### 1. Clone the repository

```bash
git clone https://github.com/mnowotka-asana/vscode-extension.git
cd vscode-extension
```

### 2. Install dependencies

```bash
npm install
```

### 3. Compile the extension

```bash
npm run compile
```

## Development

### Running the extension in development mode

1. Open the project in Visual Studio Code
2. Press `F5` or go to `Run > Start Debugging`
3. This will open a new VSCode window (Extension Development Host) with the extension loaded
4. In the Extension Development Host, open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`)
5. Type "Hello World" and select the command
6. You should see an information message "Hello World from hello-world!"

### Making changes

1. Make your changes to the TypeScript files in the `src/` directory
2. The extension will automatically recompile when you save files (if you're in watch mode)
3. Press `Ctrl+R` or `Cmd+R` in the Extension Development Host to reload the window with your changes

### Watch mode

To automatically recompile on file changes:

```bash
npm run watch
```

## Testing

### Running tests

Run all tests:

```bash
npm test
```

This command will:
1. Compile the tests
2. Compile the extension
3. Run linting
4. Execute the test suite

### Running tests in watch mode

```bash
npm run watch-tests
```

### Test structure

Tests are located in `src/test/extension.test.ts`. The test suite uses:
- Mocha as the test framework
- VSCode's test runner (@vscode/test-electron)

## Code Quality

### Linting

Run ESLint to check code style and quality:

```bash
npm run lint
```

### Type checking

TypeScript type checking is performed during compilation:

```bash
npm run compile
```

## Pre-commit Hooks

This project uses [husky](https://typicode.github.io/husky/) to run pre-commit hooks. Before each commit, the following checks are automatically executed:

- Linting (ESLint)
- Type checking (TypeScript compilation)

If any of these checks fail, the commit will be blocked until the issues are fixed.

## CI/CD

### GitHub Actions

This repository includes a GitHub Actions workflow that runs on every push and pull request to the main branch.

The CI pipeline includes:
- **Build job**: Runs on Ubuntu
  - Installs dependencies
  - Runs linting
  - Runs type checking
  - Runs tests
  
- **Test matrix job**: Runs tests on multiple platforms
  - Ubuntu (Linux)
  - Windows
  - MacOS

### Viewing CI results

You can view the CI results in the "Actions" tab of the GitHub repository.

## Building for Production

Create a production build:

```bash
npm run package
```

This creates an optimized, minified bundle in the `dist/` directory.

## Scripts Reference

| Script | Description |
|--------|-------------|
| `npm run compile` | Compile TypeScript to JavaScript |
| `npm run watch` | Watch and recompile on file changes |
| `npm run package` | Create production build |
| `npm run compile-tests` | Compile test files |
| `npm run watch-tests` | Watch and recompile test files |
| `npm test` | Run all tests |
| `npm run lint` | Run ESLint |
| `npm run pretest` | Run before tests (compile, lint) |

## Project Structure

```
.
├── .github/
│   └── workflows/
│       └── ci.yml          # GitHub Actions CI configuration
├── .husky/
│   └── pre-commit          # Pre-commit hook script
├── .vscode/
│   ├── extensions.json     # Recommended extensions
│   ├── launch.json         # Debug configuration
│   ├── settings.json       # VSCode settings
│   └── tasks.json          # Build tasks
├── src/
│   ├── test/
│   │   └── extension.test.ts  # Extension tests
│   └── extension.ts        # Main extension code
├── .gitignore
├── .vscode-test.mjs        # Test runner configuration
├── .vscodeignore           # Files to exclude from extension package
├── CHANGELOG.md            # Version history
├── eslint.config.mjs       # ESLint configuration
├── package.json            # NPM package configuration
├── README.md               # This file
├── tsconfig.json           # TypeScript configuration
└── webpack.config.js       # Webpack bundler configuration
```

## Troubleshooting

### Extension not loading

- Make sure all dependencies are installed: `npm install`
- Try recompiling: `npm run compile`
- Check the Debug Console in VSCode for error messages

### Tests failing

- Ensure you're running tests in an environment with a display (or using xvfb on Linux)
- Check that all dependencies are up to date: `npm install`
- Look for error messages in the test output

### Pre-commit hook failing

- Run the checks manually to see detailed error messages:
  - `npm run lint`
  - `npm run compile`
- Fix any reported issues before committing

## Publishing

To publish the extension to the VSCode Marketplace:

1. Install vsce: `npm install -g @vscode/vsce`
2. Package the extension: `vsce package`
3. Publish: `vsce publish`

For more information, see the [VSCode Publishing Extensions Guide](https://code.visualstudio.com/api/working-with-extensions/publishing-extension).

## Resources

- [VSCode Extension API](https://code.visualstudio.com/api)
- [Extension Guidelines](https://code.visualstudio.com/api/references/extension-guidelines)
- [Testing Extensions](https://code.visualstudio.com/api/working-with-extensions/testing-extension)

## License

MIT
