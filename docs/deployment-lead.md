# Deployment Lead

The Deployment Lead is the gatekeeper for all solution deployments across HEMY environments. No solution moves to UAT or PROD without the Deployment Lead's validation and approval.

## Responsibilities

1. **Validate solutions** before export from HEMY DEV.
2. **Import managed solutions** to HEMY UAT and HEMY PROD.
3. **Reject deployments** that fail validation checks.
4. **Maintain the deployment log** for all imports.
5. **Coordinate rollbacks** when a deployment causes issues.

## Pre-Deployment Validation Checklist

Before exporting any solution from HEMY DEV, the Deployment Lead must complete the following checks:

### 1. No Duplicate Components Across Solutions

**This is the most critical check.** Each component must exist in exactly one solution. If the same object appears in multiple solutions, the deployment is rejected.

**How to check:**

1. Open each developer's solution in HEMY DEV.
2. Compare the component lists across all active solutions.
3. Flag any component that appears in more than one solution.

**Common duplicates to watch for:**

| Component Type | Example |
|---|---|
| Forms | Case Main Form in both Solution A and Solution B |
| Views | Active Cases view in both Solution A and Solution C |
| Business Rules | Same rule added to two solutions |
| Cloud Flows | Same flow referenced in multiple solutions |
| Tables | Same table added to multiple solutions (check if only needed components are included) |

> **Note:** A table being present in multiple solutions is acceptable only if each solution adds **different components** (e.g., Solution A adds Column X, Solution B adds Column Y). What is not acceptable is the **same component** (form, view, column) existing in both.

**Resolution steps when duplicates are found:**

1. Identify which developer owns the component.
2. Remove the component from all other solutions.
3. If both developers need to modify it, one developer takes ownership and the other coordinates changes through them.


**For components already in multiple solutions**
1. We don't need to delete them unless they are causing issues in HEMY PROD
2. Usually, Forms in multiple solution and have multiple Managed Layers in PRODUCTION causes Issues like misaligned fields or duplicated lookups. These are the ones we will fix.



### 2. Solution Checker Results

1. Run **Solution Checker** on the solution in HEMY DEV.
2. All **critical** and **high-severity** issues must be resolved before export.
3. Medium and low issues should be reviewed and documented if not resolved.

### 3. Version Number

1. Confirm the solution version has been incremented.
2. Confirm the version number has never been used before.
3. Version must follow the format: `Major.Minor.Patch.Build`.

### 4. Publisher Verification

1. Confirm the solution uses the **HEMY publisher** (`hmy` prefix).
2. Reject any solution using the default publisher (`new_` prefix).

### 5. Component Completeness

1. Verify all required components are included in the solution (no missing dependencies).
2. Check that no unnecessary components have been accidentally added.
3. Confirm no components from the Default Solution have been pulled in.

### 6. Release Notes

1. Confirm the developer has provided release notes describing what changed.
2. Release notes must list all added, modified, and removed components.

## Validation Outcome

| Result | Action |
|---|---|
| All checks pass | Proceed with managed export and import to UAT |
| Duplicate components found | **Reject.** Developer must remove duplicates before re-submitting. |
| Solution Checker critical issues | **Reject.** Developer must resolve issues. |
| Missing version increment | **Reject.** Developer must update version number. |
| Wrong publisher | **Reject.** Developer must recreate components with correct publisher. |
| Missing release notes | **Hold.** Developer must provide notes before deployment proceeds. |

## Deployment Execution

**HEMY UAT**
1. In HEMY DEV, open the solution to be deployed and navigate on Pipelines
2. In the Pipeline dropdown, select **DEV-to-UAT**
3. Click on the ``Deploy Here`` button
4. The Deploying Solution window will appear on the right side, you may select Now or Later for the Deployment Schedule. Then click Next
5. This will automatically validate the solution for missing dependencies and errors.
6. If the solution contains Connection References, Enable the **Re-establish connection to activate you solution** toggle, this will let you select which connection reference in UAT you will use for your flows. 
    - For Dataverse connections you may use **Microsoft Dataverse - Shared**
    - For other connections are to be determined.
7. Write in the Deployment Notes. 

**HEMY PROD**
1. Same process as in **HEMY UAT** but change step 2 to **DEV-to-PROD** 

## Deployment Schedule

To avoid conflicts and rushed validations:

- **UAT deployments:** Scheduled times only (e.g., Tuesday and Thursday mornings). No ad-hoc imports.
- **PROD deployments:** Only after UAT sign-off. Requires at minimum 1 business day notice.
- **Emergency hotfixes:** Must still go through DEV → UAT → PROD, but validation can be expedited with team lead approval.

## What the Deployment Lead Must NOT Do

- Deploy without completing the validation checklist.
- Allow unmanaged solutions into UAT or PROD.
- Skip the duplicate component check.
- Deploy to PROD without written UAT sign-off.
- Make direct customizations in UAT or PROD to "fix" a deployment issue.
