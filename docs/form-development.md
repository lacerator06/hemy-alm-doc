# Form Development

Form conflicts are the **highest risk area** when multiple developers share an environment. Power Apps does not merge form changes — the last save wins and silently overwrites the other developer's work.

## The Golden Rule

**Never have two developers editing the same form at the same time.**

## Form Lock Register

Maintain a shared **Form Lock Register** (Excel sheet, Teams list, or Teams channel) where a developer "checks out" a form before editing and "checks in" when done.

### Register Format

| Form Name | Table | Locked By | Since | Expected Release | Purpose |
|---|---|---|---|---|---|
| Case Main Form | incident | JPT | 2026-04-28 | 2026-04-28 EOD | Adding approval tab |
| Hard Asset Main Form | msdyn_customerasset | KMA | 2026-04-28 | 2026-04-29 | New required fields |

### Lock Rules

1. **Before editing any form**, check the register. If the form is locked by another developer, do not edit it.
2. **Add your lock entry** before you begin editing.
3. **Release your lock** as soon as you finish editing and publish. Do not hold locks overnight unless necessary.
4. At **end of day**, release any locks you still hold. Post a summary of changes in the team channel.
5. If a form has been locked for more than **2 business days**, the team lead will review and resolve.

## If a Form Is Locked

When the form you need is locked by another developer:

- **Option 1:** Work on something else and wait for the lock to be released.
- **Option 2:** Coordinate with the lock holder to batch your changes together.
- **Option 3:** Create a **secondary form** for prototyping your layout and field placement. Merge your sections into the main form once the lock is released.

## Form Design Best Practices

### Split Large Forms

Where possible, break a large form into **multiple forms** so that different developers can own different forms on the same table. For example:

- `Case - Main Form` (owned by Developer A)
- `Case - Operations Form` (owned by Developer B)
- `Case - Quick Create` (owned by Developer C)

### Use Tabs for Separation

If a single form must contain many sections, organize by **tabs**. Assign tab ownership so developers know which tabs they are responsible for. Communicate this ownership in the team channel or register.

### Publish Immediately

After completing your form edits, **publish customizations immediately**. Unpublished form changes are invisible to other developers and will cause confusion when they open the form editor.

## What NOT to Do

- Do not edit a form that is locked by another developer.
- Do not hold form locks for more than 2 business days without team lead approval.
- Do not leave customizations unpublished at end of day.
- Do not delete tabs or sections created by another developer without their approval.
- Do not rearrange fields on a tab owned by another developer.
