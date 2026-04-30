# Conflict Resolution

Even with good practices, conflicts will happen. This page defines how to identify, resolve, and prevent recurring conflicts.

## Accidental Overwrites

If two developers accidentally modify the same component (form, view, business rule, etc.):

1. The **second developer to publish** must verify that the first developer's changes are still intact.
2. If changes were overwritten, restore from the **solution zip backup** — this is why versioned exports are critical.
3. The two developers must coordinate to merge both sets of changes manually.
4. Update the Form Lock Register or team channel to prevent the same conflict from happening again.

## Disputed Ownership

If two developers disagree about who should own or modify a component:

1. Check the [Naming Conventions](naming-conventions.md) — the developer whose initials are in the component name is the designated owner.
2. If ownership is unclear, the **team lead** decides.
3. Never resolve a dispute by overwriting the other developer's work.

## Broken Deployments

If a managed solution import to UAT or PROD fails:

1. **Do not attempt to fix the issue in UAT or PROD.**
2. Review the import error log to identify the cause.
3. Common causes:
   - Missing dependency (a component references something that does not exist in the target environment)
   - Version conflict (an older version imported over a newer one)
   - Schema mismatch (a column type was changed in DEV but the target still has the old type)
4. Fix the issue in **HEMY DEV**, increment the solution version, and re-export.
5. Re-import the corrected solution to UAT for testing.

## Unmanaged Components in UAT or PROD

If unmanaged customizations are discovered in UAT or PROD:

1. **Do not delete them immediately** — they may be supporting active functionality.
2. Identify who created them and why.
3. Recreate the component properly in HEMY DEV inside a solution.
4. Deploy the managed version to UAT/PROD, which will overlay the unmanaged component.
5. Document the incident and reinforce the rule: no direct customizations in UAT or PROD.

## Escalation Path

| Situation | First Action | Escalate To |
|---|---|---|
| Form overwrite | Restore from backup, coordinate with other developer | Team Lead |
| Ownership dispute | Check naming conventions | Team Lead |
| Failed deployment | Review error log, fix in DEV | Deployment Lead |
| Unmanaged component in UAT/PROD | Identify owner, recreate in DEV | Team Lead |
| Repeated rule violations | Peer discussion | Team Lead / Management |

## Prevention

The best conflict resolution is prevention:

- **Use the Form Lock Register** consistently.
- **Announce your work** in the team channel before starting.
- **Publish frequently** so others can see your changes.
- **Export solution backups** regularly so overwrites can be reversed.
- **Attend the weekly sync** to surface potential conflicts early.
