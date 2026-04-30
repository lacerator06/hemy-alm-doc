<div align="right">

**Created by:** Leonard Estrada  
**Date Created:** April 28, 2026

</div>

# Introduction

## Purpose

This documentation defines the collaboration rules and application lifecycle management (ALM) standards for all Power Apps developers working across the HEMY environments.

## Why These Rules Exist

Multiple developers work on Model-driven apps within the same shared environments. Without clear rules, the following problems will occur:

- **Silent overwrites** — The last developer to save a form wins. Previous changes are lost without warning.
- **Orphaned components** — Tables, columns, and flows created outside of solutions become unmanageable.
- **Broken deployments** — Unmanaged solutions imported into UAT or PROD create dependency issues that are difficult to reverse.
- **Untraceable changes** — Without naming conventions and ownership, no one knows who changed what or why.

## Environment Overview

The HEMY platform uses four environments arranged in a promotion pipeline:

```
HEMY EXPLORATION ──► HEMY DEV ──► HEMY UAT ──► HEMY PROD
   (Prototype)      (Build)      (Test)      (Live)
```

- **HEMY EXPLORATION** — Sandbox for testing feasibility. Everything here is disposable.
- **HEMY DEV** — The primary development environment. All production-bound work starts here inside proper solutions.
- **HEMY UAT** — Receives managed solution imports from DEV. Used for testing only. No direct changes allowed.
- **HEMY PROD** — The live environment. Only managed solutions that have passed UAT testing are deployed here.

## Scope

These rules apply to all developers building or modifying:

- Model-driven apps
- Tables, columns, and relationships
- Forms, views, and dashboards
- Business rules and classic workflows
- Cloud flows (Power Automate)
- Security roles
- Plugins and custom code
- Canvas apps embedded in Model-driven apps
