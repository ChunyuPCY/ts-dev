# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **TypeScript monorepo template** using pnpm workspaces with catalog mode. It's configured as a development environment for building TypeScript applications and libraries, but currently contains no application code - only infrastructure setup.

## Development Environment

### Prerequisites
- **Node.js**: >=20.0.0
- **Package Manager**: pnpm >=10.0.0 (catalog mode enabled)
- **VS Code Extensions**: Recommended extensions are in `.vscode/extensions.json`

### Workspace Structure
```
/
├── apps/              # Applications (empty - planned)
├── internal/          # Shared configurations
│   └── tsconfig/     # TypeScript configurations
├── packages/          # Libraries (doesn't exist yet - planned)
├── scripts/          # Build scripts (empty - planned)
└── node_modules/
```

### Package Management
- Uses **pnpm workspaces** with **catalog mode** (`catalogMode: prefer`)
- Dependencies are organized into catalogs: `cli`, `vue`, `inlined`, `testing`, `types`
- Root `package.json` contains development scripts and workspace configuration

## Development Commands

### Common Tasks
```bash
# Install dependencies
pnpm install

# Lint code (ESLint configuration currently empty)
pnpm lint
pnpm lint:fix

# Validate commit messages
pnpm commitlint

# Setup git hooks (runs automatically after install)
pnpm prepare
```

### Git Hooks
- **pre-commit**: Runs `pnpm lint-staged` to lint staged files
- **commit-msg**: Validates commit messages using commitlint

### Testing
- **Test Framework**: Vitest (configured in catalog, no tests exist yet)
- **Additional Tools**: `vitest-package-exports`, `tinyexec`, `yaml`

## TypeScript Configuration

### Configuration Strategy
- **Base config**: `internal/tsconfig/base.json` - Strict TypeScript settings
- **Environment extensions**:
  - `web.json` - Web projects (Vue.js oriented)
  - `node.json` - Node.js projects
  - `react.json` - React projects
  - `library.json` - Library projects
  - `package.json` - Package-specific settings

### Key Compiler Options
- Target: `ESNext`
- Module: `ESNext`
- Strict mode enabled with `noUncheckedIndexedAccess`
- `verbatimModuleSyntax`: true
- `isolatedModules`: true

## Commit Convention

### Commit Types
Standard conventional commit types plus extensions:
- **Standard**: `feat`, `fix`, `perf`, `style`, `docs`, `test`, `refactor`, `build`, `ci`, `chore`, `revert`
- **Extended**: `wip`, `workflow`, `types`, `release`

### Validation
- Commit messages are validated by commitlint
- Configuration in `commitlint.config.ts`

## Code Quality

### Current Setup
- **ESLint**: Configured but empty config (`eslint.config.mjs`)
- **Spell Checking**: cspell with custom word list (`cspell.json`)
- **Pre-commit Hooks**: Lint staged files automatically

### Planned Infrastructure (from README TODO)
- [ ] Lint configuration
- [ ] Formatter setup
- [ ] cspell word management
- [ ] CSS framework integration
- [ ] Test framework setup
- [ ] Git hooks configuration

## Architecture Notes

### Monorepo Design
- **Internal packages**: Shared configurations in `internal/`
- **Applications**: Frontend/backend apps in `apps/` (planned)
- **Packages**: Reusable libraries in `packages/` (planned)
- **Scripts**: Build/utility scripts in `scripts/` (planned)

### Build Tools
- **Primary**: Vite (for web applications)
- **TypeScript Execution**: tsx
- **Package Building**: tsdown
- **Version Management**: bumpp
- **Package Validation**: publint

### Development Philosophy
- Modern JavaScript/TypeScript ecosystem
- Tooling-focused with comprehensive dev experience
- VS Code integration with recommended extensions
- Monorepo-friendly with pnpm workspaces and catalog mode

## Project Status

This is a **newly initialized template** with comprehensive infrastructure but no application code. The repository is ready for:
1. Adding applications to `apps/` directory
2. Creating shared libraries in `packages/` directory
3. Configuring linting rules in `eslint.config.mjs`
4. Setting up test files and configurations
5. Implementing build scripts in `scripts/`

All TypeScript configurations are pre-configured for different project types (web, node, react, library).