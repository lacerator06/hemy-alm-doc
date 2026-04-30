# Deployment Flow

This page defines how solutions move from HEMY DEV through UAT and into PROD.

## Pipeline Overview

```
HEMY DEV (unmanaged solutions per developer)
    │
    ├── Merge components into master unmanaged solution
    │
    ├── Export as MANAGED solution (.zip)
    │
    ├── Store .zip in shared repository with version number
    │
    ▼
HEMY UAT (import managed solution)
    │
    ├── Functional testing and user acceptance testing
    │
    ├── Bugs? → Fix in DEV → Re-export → Re-import to UAT
    │
    ├── Testing sign-off
    │
    ▼
HEMY PROD (import same managed solution)
    │
    └── Deployment log updated
```

## Step-by-Step Process

### 1. Prepare in HEMY DEV

1. Verify all components are inside your unmanaged solution.
2. Test your changes in DEV to confirm basic functionality.

### 2. Preparing Master Solution in HEMY DEV
    
**Developers**

1. Inform the Deployment Lead about the developments done
2. List all the components to be added in the Master Solution.
3. Provide the link of all the component

**Deployment Lead**

1. Review the development and suggest improvements if necessary.
2. **Add to Solution** all the components provided by the Developers to the Master Solution.
3. Follow the Deployment Execution from [Deployment Lead](deployment-lead.md#deployment-execution).


### 3. UAT Testing

1. Testers execute test cases against the new functionality.
2. Bugs and issues are logged and sent back to developers.
3. Developers fix bugs in **HEMY DEV**, increment the version, and repeat steps 2-3.
4. When all tests pass, the test lead provides **written sign-off**.

### 5. Deploy to HEMY PROD

1. Only after UAT sign-off is received.
2. Only the **designated deployment lead** deploys to PROD.
3. Follow the Deployment Execution from [Deployment Lead](deployment-lead.md#deployment-execution).
## Deployment Log

Maintain a deployment log (SharePoint list or Excel file) with the following fields:

| Field | Description |
|---|---|
| Date | Deployment date and time |
| Solution Name | Full solution name with version |
| Deployed By | Name of the deployment lead |
| Environment | Target environment (UAT or PROD) |
| Sign-off By | Name of the person who authorized the deployment |
| Release Notes | Summary of changes or link to detailed notes |
| Status | Success / Failed / Rolled Back |

## Rollback

If a deployment to PROD causes issues:

1. **Do not attempt to fix directly in PROD.**
2. Import the **previous managed solution version** to roll back.
3. Investigate and fix the issue in DEV.
4. Follow the full deployment pipeline again (DEV → UAT → PROD).

## What NOT to Do

- Do not import unmanaged solutions into UAT or PROD.
- Do not skip UAT and deploy directly from DEV to PROD.
- Do not reuse version numbers.
- Do not deploy without written UAT sign-off.
- Do not re-export from DEV after UAT sign-off — use the same `.zip` that was tested.
