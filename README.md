# @qvlt/config-prettier

Prettier configuration for Qvlt projects.

## Installation

```bash
npm install --save-dev @qvlt/config-prettier
# or
pnpm add --save-dev @qvlt/config-prettier
# or
yarn add --dev @qvlt/config-prettier
```

**Note**: `prettier` is included as a dependency, so you don't need to install it separately.

## Usage

### Basic Configuration

Create a `prettier.config.js` file in your project root:

**ES Modules (recommended):**

```javascript
import config from '@qvlt/config-prettier';

export default config;
```

**CommonJS:**

```javascript
// prettier.config.cjs
module.exports = require('@qvlt/config-prettier');
```

The package supports both ESM and CommonJS exports, so it works with any project setup.

See the `example/` directory for complete working examples.

### With Ignore Patterns

Prettier uses a separate ignore file. You can reference the shared ignore patterns:

```bash
# Use the shared ignore file
prettier --ignore-path node_modules/@qvlt/config-prettier/ignore --write .
```

### Package.json Scripts

Add these scripts to your `package.json`:

```json
{
  "scripts": {
    "format": "prettier --ignore-path node_modules/@qvlt/config-prettier/ignore --write .",
    "format:check": "prettier --ignore-path node_modules/@qvlt/config-prettier/ignore --check ."
  }
}
```

**Note**: If you already have a `.prettierignore` file, you have two options:

1. **Merge approach (recommended)**: Copy the shared ignore into your repo's `.prettierignore` and append local entries:

   ```bash
   cp node_modules/@qvlt/config-prettier/ignore .prettierignore
   # then add repo-specific patterns to .prettierignore
   ```

   Then you can use standard Prettier commands without `--ignore-path`.

2. **Override approach**: Keep using `--ignore-path` and maintain a single ignore file.

## Configuration Details

This configuration is based on the settings from `apps/web` and includes:

### Code Formatting

- **Semicolons**: Always added (`semi: true`)
- **Quotes**: Single quotes (`singleQuote: true`)
- **Trailing commas**: All (`trailingComma: 'all'`)
- **Line width**: 120 characters (`printWidth: 120`)
- **Indentation**: 2 spaces (`tabWidth: 2`)
- **Arrow function parentheses**: Always (`arrowParens: 'always'`)

### JSX/TSX Support

- **JSX quotes**: Single quotes (`jsxSingleQuote: true`)
- **Bracket same line**: False (`bracketSameLine: false`)

### File Handling

- **End of line**: LF (`endOfLine: 'lf'`) for cross-platform consistency
- **Quote properties**: As needed (`quoteProps: 'as-needed'`)
- **Prose wrap**: Preserve (`proseWrap: 'preserve'`)

## Ignore Patterns

The ignore configuration excludes common files and directories. Prettier uses a separate ignore file:

- **Text file**: `node_modules/@qvlt/config-prettier/ignore` - Use with `--ignore-path`

- **Dependencies**: `node_modules/`, lock files
- **Build outputs**: `dist/`, `build/`, `*.tsbuildinfo`
- **Environment files**: `.env*` files
- **IDE files**: `.vscode/`, `.idea/`
- **OS files**: `.DS_Store`, `Thumbs.db`
- **Logs**: `*.log`, `logs/`
- **Coverage**: `coverage/`, `*.lcov`
- **Generated files**: `*.min.js`, `src/generated/`
- **Cache directories**: Various build tool caches

## Integration with ESLint

This Prettier configuration is designed to work seamlessly with `@qvlt/config-eslint`. The ESLint config includes `eslint-config-prettier` to disable conflicting rules.

## Examples

### Before Formatting

```javascript
const example = {
  name: 'test',
  items: [1, 2, 3],
  func: (x, y) => {
    return x + y;
  },
};
```

### After Formatting

```javascript
const example = {
  name: 'test',
  items: [1, 2, 3],
  func: (x, y) => {
    return x + y;
  },
};
```

## Version Compatibility

- **Node.js**: >=18.18.0
- **Prettier**: ^3.0.0

## Contributing

Want to help? See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.
## License

MIT
