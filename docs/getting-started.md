# Getting Started

This page walks new developers through the initial setup required before starting work in the HEMY environments.

## Prerequisites

- Access to all four HEMY environments (EXPLORATION, DEV, UAT, PROD)
- Membership in the designated Teams channel for development coordination
- Access to the shared repository for solution backups (SharePoint or Azure DevOps)
- Access to the Form Lock Register

## First-Time Setup in HEMY DEV

### 1. Verify the Publisher

Before creating any components, confirm that the **HEMY publisher** is available in HEMY DEV:

| Setting | Value |
|---|---|
| Display Name | Hemy (HEMY) |
| Name | HEMY |
| Prefix | `hmy` |

If the publisher does not exist, contact the team lead. **Do not create your own publisher** and never use the default publisher.

### 2. Create Your Solution

Create a new unmanaged solution for your feature or module:

- **Display Name:** `HEMY <Your Initials>` (e.g., `HEMY LE`)
- **Name:** `HEMY_<Initials>` (e.g., `HEMY_JD`)
- **Publisher:** Select the HEMY publisher (`HEMY`)
- **Version:** Start at `1.0.0.0`

### 3. Familiarize Yourself with Existing Components

Before creating new components:

1. Review the existing tables, forms, and flows in the environment.
2. Check other devlopers' solutions to understand what is already being worked on.
3. Ask in the team channel if you are unsure whether a component already exists.
4. Consult with NS|LE about the development and before doing anything.
## Before Your First Day of Work

1. Read all pages in this documentation, especially:
   - [Environment Guidelines](environment-guidelines.md)
   - [Form Development](form-development.md)
   - [Naming Conventions](naming-conventions.md)
2. Bookmark the Form Lock Register.
3. Join the designated Teams channel and introduce yourself.
4. Confirm your access to the shared solution backup repository.

## Checklist

- [ ] I have access to all four HEMY environments
- [ ] I have joined the Teams development channel
- [ ] I have access to the Form Lock Register
- [ ] I have access to the shared solution backup repository
- [ ] I have verified the HEMY publisher exists in DEV
- [ ] I have created my personal unmanaged solution in DEV
- [ ] I have read all pages in this documentation
