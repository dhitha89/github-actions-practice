# GitHub Actions Practice

A learning repository to understand and practice GitHub Actions workflows.

## Overview

This repository contains example workflows demonstrating different GitHub Actions triggers, jobs, steps, and best practices.

### Workflow Anatomy

```yaml
name: Workflow Name                    # Human-readable workflow name

on:                                    # Trigger events
  push:
    branches: [main]
  pull_request:
    types: [opened, synchronize]

jobs:                                  # Container for all jobs
  job-name:                            # Unique job identifier
    runs-on: ubuntu-latest             # Runner environment
    steps:                             # Sequential tasks
      - name: Step Name                # Human-readable step label
        uses: owner/action@version     # Reusable GitHub Action
      
      - name: Another Step
        run: command here              # Execute shell command
```

### Key Concepts

| Key | Purpose | Example |
|-----|---------|---------|
| `on:` | Defines workflow triggers | `push`, `pull_request`, `schedule` |
| `jobs:` | Container for parallel/sequential jobs | `build`, `test`, `deploy` |
| `runs-on:` | Specifies the runner environment | `ubuntu-latest`, `windows-latest` |
| `steps:` | List of tasks in a job | Checkout, build, test steps |
| `uses:` | Runs a pre-built reusable action | `actions/checkout@v4` |
| `run:` | Executes shell commands | `echo "Hello"`, `npm test` |
| `name:` | Human-readable label (on steps) | For logging and UI display |

### GitHub Context Variables

- `${{ github.ref_name }}` - Branch or tag name (current context)
- `${{ github.head_ref }}` - Head branch in PR (source branch)
- `${{ github.base_ref }}` - Base branch in PR (target branch)
- `${{ github.event_name }}` - Event that triggered the workflow

## 🔧 Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/dhitha89/github-actions-practice.git
   cd github-actions-practice
   ```

2. **Create a feature branch:**
   ```bash
   git checkout -b feature-test
   ```

3. **Make changes and commit:**
   ```bash
   git add .
   git commit -m "Add changes"
   ```

4. **Push and create a PR:**
   ```bash
   git push origin feature-test
   ```

5. **Watch workflows run:**
    - Go to the **Actions** tab
    - See both workflows in action

### Running Multiple Commands in One Step

```yaml
- name: Multiple commands
  run: |
    echo "Command 1"
    echo "Command 2"
    echo "Command 3"
```

### Conditional Steps

```yaml
- name: Step with condition
  if: github.ref == 'refs/heads/main'
  run: echo "This only runs on main"
```

### Using Environment Variables

```yaml
- name: Use environment variable
  env:
    MY_VAR: "value"
  run: echo $MY_VAR
```

## Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow Syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [Available Actions](https://github.com/actions)
