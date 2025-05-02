# Secrets Prevention with Pre-commit Hooks

This repository is configured with pre-commit hooks to prevent accidentally committing secrets and sensitive information.

## Setup

1. Ensure you have Python and Go installed
2. Install pre-commit and necessary tools:
   ```
   pip install pre-commit detect-secrets
   go install github.com/gitleaks/gitleaks@latest
   ```
3. Install the pre-commit hooks:
   ```
   pre-commit install
   ```

## How It Works

The pre-commit hooks will automatically scan your code before each commit to detect:
- API keys
- Access tokens
- Private keys
- Passwords
- Other sensitive information

If a potential secret is found, the commit will be blocked and you'll see information about the detected secret.

## What to Do When a Secret is Detected

1. Remove the secret from your code
2. Consider using environment variables or a secure secret management system
3. If you've accidentally committed a secret in the past, consider it compromised and rotate it

## Baseline

The repository includes a `.secrets.baseline` file which contains allowlisted secrets that have been reviewed.
To update this baseline:

```
detect-secrets scan > .secrets.baseline
```

## Test

You can test the pre-commit hooks by trying to commit the `test_secrets.py` file, which contains a fake API key.
