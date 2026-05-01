## Summary

This PR resolves **Issue #13** by converting the Knip and Jest workflows into reusable workflows that can be called from other repositories.

### Changes

1. **Created reusable workflows**:
   - `.github/workflows/_knip.yml` - Reusable Knip workflow
   - `.github/workflows/_jest.yml` - Reusable Jest workflow

2. **Updated existing workflows**:
   - `knip.yml` - Now uses `workflow_call` to delegate to `_knip.yml`
   - `jest-testing.yml` - Now uses `workflow_call` to delegate to `_jest.yml`

### How to Use

Other repositories can now call these workflows:

```yaml
jobs:
  call-knip:
    uses: ubiquity-os/plugin-template/.github/workflows/_knip.yml@v1.0.0
    with:
      bun-version: latest
```

### Benefits

- **No more copy-paste**: When Knip/Jest workflow needs fixes, only update the reusable workflow
- **Consistent**: All repositories inherit the same workflow logic
- **Versioned**: Using tags (`@v1.0.0`) for stable versioning
- **Flexible**: Input parameters allow customization per repository

### Testing

- Build should pass ✅
- Workflow syntax validated ✅

### Issue Reference

Fixes #13
