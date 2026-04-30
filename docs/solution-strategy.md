# Solution Strategy

Solutions are the foundation of organized development in Power Apps. Every developer must follow these rules to avoid conflicts and ensure clean deployments.

## Core Rule

**Every developer must work inside their own unmanaged solution in HEMY DEV.** Never customize components directly in the Default Solution.

## Solution Structure

### Per-Developer Solutions

Each developer creates their own unmanaged solution for the feature or module they are working on.

**Naming format:** `HEMY_<DevInitials>`

Examples:
- `HEMY_LE`

### Master Release Solution

When features are ready for deployment, components are consolidated into a single **master unmanaged solution** before exporting.
These Solutions are the Main solutions to be deployed using Pipelines

**Naming format:** `Name_of_Solution_v<Major>.<Minor>.<Patch>.<Build>`

Examples:
- `HEMY_P61 Budget Reporting_v1.0.0.1`
    - Each Deployment will automatically update the Build #
- `HEMY_P61 Budget Reporting_v1.2.0.0`
    - A new solution is recommended to be created when there is a major change. 

## Publisher

All developers must use the **same publisher** to ensure consistent prefixes across all components.

| Setting | Value |
|---|---|
| Display Name | Hemy |
| Name | HEMY |
| Prefix | `hmy` |


> **Moving forward, the use of the default publisher** (`new_` prefix) is not allowed. Components created with the wrong prefix cannot be easily renamed and will cause long-term maintenance issues.

## Before Starting Work

Before adding a component to your solution, check the following:

1. **Does the component already exist** in the environment? If so, another developer may own it.
2. **Is the component already in another developer's solution?** If yes, coordinate with that developer before adding it to yours.
3. **Is a form or shared component locked?** Check the [Form Lock Register](form-development.md#form-lock-register).

## Solution Export Rules

- **Export as managed** when deploying to UAT and PROD.
- **Version your solutions** using semantic versioning (`Major.Minor.Patch.Build`). Never reuse a version number.
- Store exported solution `.zip` files in the **shared repository** (SharePoint or Azure DevOps) with the version number and export date.
- Include release notes describing what changed in each version.

## No Duplicate Components Across Solutions

**A component must exist in only one developer's solution at any given time.** If a component already lives in another solution, it must not be added to yours.

### Why This Matters

When the same component (e.g., Case Main Form) exists in multiple solutions, deploying those solutions creates unpredictable results. The last solution imported wins, silently overwriting changes from the other. This makes deployments unreliable and changes untraceable.

### Rule

| Scenario | Action |
|---|---|
| Component exists in Solution A | Do **not** add it to Solution B |
| You need to modify a component in another solution | Coordinate with the owner of that solution |
| A component must move between solutions | Remove it from the original solution first, then add it to the new one |

### Enforcement

The **Deployment Lead** validates every solution before export. If duplicate components are found across solutions, the deployment will be **rejected** until the duplication is resolved. See the [Deployment Lead](deployment-lead.md) page for the full validation checklist.

### Example

> Developer A has `Case Main Form` in `HEMY_CaseManagement_DA`.
>
> Developer B needs to add fields to the same form. Developer B must **not** add `Case Main Form` to `HEMY_Escalation_DB`. Instead, Developer B coordinates with Developer A, or the form is transferred to Developer B's solution after being removed from Developer A's.

## Component Ownership

- The developer who creates a component is its **owner** and is responsible for its maintenance.
- Do not modify, rename, or delete another developer's components without their explicit approval.
- If a component needs to be shared across multiple developer solutions, agree on a single owner who is responsible for changes to that component.
