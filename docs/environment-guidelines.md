# Environment Guidelines

Each environment has a specific purpose and set of rules. Developers must respect the boundaries of each environment.

## HEMY EXPLORATION

**Purpose:** Proof of concept and feasibility testing.

### Rules

- Developers may experiment freely without formal solution structure.
- Treat everything in this environment as **disposable**. Do not build production-quality logic here.
- **Document what worked** (screenshots, notes, configuration details) before anything is cleaned up or abandoned.
- Abandoned POCs must be cleaned up monthly to avoid clutter.
- Findings and validated concepts from EXPLORATION must be **rebuilt from scratch** in HEMY DEV — do not export unmanaged solutions from EXPLORATION into DEV.

### What Is Allowed

- Creating tables, forms, and flows for testing purposes
- Rapid prototyping without naming conventions
- Testing third-party connectors and integrations

### What Is NOT Allowed

- Treating EXPLORATION as the development environment
- Exporting solutions from EXPLORATION directly into UAT or PROD

---

## HEMY DEV

**Purpose:** Primary development environment where validated concepts are properly built.

### Rules

- All work must be done inside a **named unmanaged solution** (see [Solution Strategy](solution-strategy.md)).
- Use the standard **publisher prefix** (`hmy_`). Never use the default `new_` prefix.
- Do not create tables, columns, or any components outside of a solution.
- Do not delete or rename another developer's components without their approval.
- Publish your customizations immediately after completing a unit of work. Unpublished changes are invisible to others and create confusion.
- Follow all [Naming Conventions](naming-conventions.md).

### What Is Allowed

- Creating and modifying components inside your own unmanaged solution
- Adding shared components to your solution (after checking the [Form Lock Register](form-development.md#form-lock-register))
- Exporting managed solutions for deployment to UAT

### What Is NOT Allowed

- Working in the Default Solution
- Creating components without adding them to a solution
- Directly modifying another developer's solution without coordination

---

## HEMY UAT

**Purpose:** Testing environment. Receives managed solution imports from DEV.

### Rules

- **No direct changes are allowed in UAT.** All changes arrive via managed solution import from DEV.
- Only testers and the **designated deployment lead** operate in this environment.
- Bugs found during UAT testing are fixed in **HEMY DEV**, re-exported, and re-imported to UAT.
- Never hotfix directly in UAT.

### What Is Allowed

- Importing managed solutions from DEV
- Functional testing and user acceptance testing
- Logging bugs and feedback for developers to fix in DEV

### What Is NOT Allowed

- Creating or modifying any components directly
- Importing unmanaged solutions
- Applying quick fixes or workarounds directly in UAT

---

## HEMY PROD

**Purpose:** Live production environment.

### Rules

- **Strictly managed solutions only.** No unmanaged customizations, ever.
- Deployments require **sign-off from UAT testing** before import.
- Only the **designated deployment lead** (or CI/CD pipeline) imports solutions.
- A **deployment log** must be maintained: who deployed what, when, and which solution version.

### What Is Allowed

- Importing managed solutions that have passed UAT sign-off
- Monitoring and observing application behavior

### What Is NOT Allowed

- Any direct customization or component creation
- Importing unmanaged solutions
- Skipping UAT and deploying directly from DEV
- Any developer deploying without deployment lead authorization
