# Daily Collaboration Protocol

These are the day-to-day practices every developer must follow to avoid conflicts in the shared environments.

## Start of Day

1. **Check the Form Lock Register** for any active locks on forms you plan to work on.
2. **Read the team channel** for announcements, ongoing deployments, or warnings from other developers.
3. **Plan your work** and announce what components you intend to modify today.

## Before Editing a Shared Component

1. **Announce in the team channel** which component you are about to edit (form, view, business rule, flow, etc.).
2. **Wait for acknowledgment** if another developer recently worked on the same component.
3. **Lock the form** in the Form Lock Register if you are editing a form (see [Form Development](form-development.md)).
4. **Check the component** in the form editor or solution to confirm no unpublished changes from another developer are pending.

## During Development

1. Work inside **your own unmanaged solution** at all times.
2. Save and publish frequently — small incremental publishes are safer than large batches.
3. If you discover a conflict or unexpected change to a component, **stop and notify the team** before proceeding.
4. Follow all [Naming Conventions](naming-conventions.md).

## After Completing a Unit of Work

1. **Publish your customizations immediately.** Unpublished changes are invisible to other developers.
2. **Release any form locks** you no longer need.
3. **Test your changes** in DEV to confirm basic functionality.
4. Notify the team channel if your changes affect shared components.

## End of Day

1. **Publish all pending customizations.** Do not leave unpublished changes overnight.
2. **Release all form locks** you hold. If you must hold a lock overnight, notify the team with an explanation.
3. **Post a brief summary** of what you changed today in the team channel. Example:

   > "Updated Case Main Form — added Approval tab with 3 new fields. Updated business rule for auto-status. Lock released."

## Communication Expectations

- Use the designated **Teams channel** for all development announcements.
- **Respond promptly** when another developer asks about a component you own or have locked.
- If you will be absent, **release all locks** and notify the team of any in-progress work that others may need to continue.

## Weekly Sync

Hold a brief weekly sync meeting (15-30 minutes) to:

- Review active development work and upcoming changes
- Identify potential conflicts before they happen
- Plan deployments to UAT
- Clean up abandoned solutions or components in DEV and EXPLORATION
