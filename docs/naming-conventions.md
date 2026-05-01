# Naming Conventions

Consistent naming makes components traceable, reduces confusion, and ensures smooth deployments. All developers must follow these conventions in **HEMY DEV**.

## Summary Table

| Asset | Convention | Example |
|---|---|---|
| Solution (per-developer) | `HEMY_<Initials>` | `HEMY_LE` |
| Solution (release) | `HEMY_SolutionName_v<Version>` | `HEMY_P29 Ordering Process_v1.2.0.0` |
| Publisher prefix | `hmy_` | `hmy_` |
| Table | `hmy_<entityname>` | `hmy_new_table` |
| Column | `hmy_<columnname>` | `hmy_new_column` |
| Form | `<Table Display Name> - <Purpose>` | `Case - Main Form` |
| View | `<Table Display Name> - <Description>` | `Case - Active Cases by ` |
| Business Rule | `<Initials> - <Description>` | `LE - Set Purchase Order Status to Paid` |
| Classic Workflow | `HEMY - <Module> - <Action>` | `HEMY - Cases - Fetch Owner Business from Customer` |
| Cloud Flow | `HEMY - <Module> - <Action>` | `HEMY - Purchase Orders - Send Email on Approval` |
| Web Resource | `hmy_/scripts/<name>.js` | `hmy_/scripts/hardasset_form.js` |

## Rules

1. **Always use the `hmy_` publisher prefix.** Never use the default `new_` prefix.
2. **Table and column names** use lowercase with no spaces. Use descriptive names that reflect the business purpose.
3. **Display names** use proper casing and spaces for readability.
4. **Business rules and workflows** must include the developer's initials so changes can be traced back to the responsible developer.
5. **Cloud flows** must start with `HEMY` followed by the module name for easy filtering and identification.
6. **Never rename** an existing component's schema name after creation — this breaks dependencies. If a name is wrong, coordinate with the team before taking action.
7. **Avoid abbreviations** in display names unless they are universally understood within the team (e.g., `UAT`, `API`).
