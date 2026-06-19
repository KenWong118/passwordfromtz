# CBOM Generation

This repository includes a manual GitHub Actions workflow to generate a CycloneDX CBOM for the Java project and commit the updated `cbom16.json` file back to the repository.

## Output

The workflow generates:

- `cbom16.json`

using this command:

```bash
cdxgen --type java --include-crypto --evidence --deep --spec-version 1.6 --profile appsec -o cbom16.json
```

## Manual workflow

The workflow is intended to be run manually from the GitHub Actions UI using `workflow_dispatch`.

Suggested workflow file path:

- `.github/workflows/generate-cbom.yml`

## What the workflow does

1. Checks out the repository
2. Sets up Node.js
3. Installs `@cyclonedx/cdxgen`
4. Runs cdxgen to generate `cbom16.json`
5. Commits and pushes the updated `cbom16.json` back to the current branch

## Notes

- The workflow requires repository write permission to push changes.
- If no changes are detected in `cbom16.json`, the commit step should do nothing.
- SSH is not required inside GitHub Actions when using the default `GITHUB_TOKEN` with contents write permission.
