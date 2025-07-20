# Context Engineering Workflow: User Guide

Welcome to the Context Engineering workflow! This guide provides a comprehensive overview of how to use this system to manage complex software projects from idea to deployment and maintenance.

## 1. Getting Started

### Starting a New Project

1.  **Clone the Repository:** Start by cloning this repository into a new, empty folder for your project.
    ```bash
    git clone <repository_url> my-new-project
    cd my-new-project
    ```
2.  **Clear Old Data:** To ensure a clean start, you need to remove the sample project data.
    *   Delete the contents of `PROJECT.md` but keep the file and its headers.
    *   Remove all files inside the `docs/prps/` directory, but leave the `templates` subdirectory untouched.
    *   Delete the `docs/vision/vision.md` and `docs/vision/architecture-review.md` files if they exist.

## 2. Command Reference

This table lists all the commands available in the workflow.

| Command | Purpose & Typical Use Case |
| :--- | :--- |
| `brainstorm-vision` | An interactive session to transform a raw idea into a structured project vision (`vision.md`). Use this at the very beginning of a project when you only have a high-level concept. |
| `refine-architecture` | An interactive review of the `vision.md` file to stress-test the concept, identify risks, and challenge assumptions before planning begins. Use this immediately after creating the vision. |
| `init-project` | Automatically populates the `PROJECT.md` roadmap and creates stub PRP files for every feature defined in the `vision.md`. Use this once the vision and architecture are stable. |
| `generate-prp` | An interactive session to flesh out a stub PRP with detailed research, code examples, a technical plan, and validation steps. Use this for each feature before development starts. |
| `execute-prp` | The primary coding runtime - implement your PRP to specification. |
| `audit-codebase` | Scans the codebase for dead code, stale dependencies, and complexity hotspots, generating a timestamped report. Use this periodically to maintain code health. |
| `deprecate-feature` | A guided process to safely remove a feature and its dependencies from the codebase. Use this when a feature is no longer needed or is being replaced. |
| `re-architect` | Compares the original vision to the current state of the code, identifies architectural drift, and helps you create a plan to either realign the code or update the vision. Use this when the project feels like it's deviating from its intended path. |

## 3. Core Workflow & Scenarios

This workflow is designed to be flexible. Here’s how to adapt it to different starting points.

### The Ideal Workflow (from scratch)

1.  **Vision:** Start with `brainstorm-vision` to create `docs/vision/vision.md`.
2.  **Architecture:** Immediately follow up with `refine-architecture` to harden the vision.
3.  **Initialization:** Run `init-project` to create the project structure.
4.  **Planning:** For each feature in your `PROJECT.md` roadmap, run `generate-prp` to create a detailed plan.
5.  **Implementation:** Write the code with `execute-prp` to implement the feature as described in the PRP.
6.  **Repeat:** Continue generating PRPs and implementing features until the project is complete.

### Scenario A: The Blank Slate

You have a raw idea and nothing else.

1.  Follow the **Ideal Workflow** described above. The `brainstorm-vision` command is designed specifically for this scenario, helping you build the foundational context from scratch.

### Scenario B: The Head Start

You have existing code, notes, or other project artifacts.

1.  **Consolidate:** Gather all your existing materials.
2.  **Synthesize into Vision:** Instead of starting with `brainstorm-vision`, manually create the `docs/vision/vision.md` file by filling out the `VISION_TEMPLATE.md`. Use your existing notes and code to inform the Mission, Objectives, and Projects/Phases.
3.  **Incorporate into PRPs:** When you run `generate-prp` for a feature, use your existing code as the primary source for the "Code Examples" and "Implementation Blueprint" sections. This ensures the new work is consistent with the old.

### Scenario C: The Return

You are returning to a project after a long break and need to get re-oriented.

1.  **Audit First:** Run `audit-codebase`. This will give you an immediate, objective snapshot of the code's health, pointing out unused code or dependencies that might have been left behind.
2.  **Review Architecture:** Run `re-architect`. This is the most critical step. It will show you exactly how the code's current state differs from the original plan, allowing you to understand what has changed and why.
3.  **Formulate a Plan:** Based on the output of `re-architect`, decide whether to update the vision or refactor the code. The command will help you create the necessary PRPs to get back on track safely.

## 4. The Rhythm of Development

Knowing *when* to use each command is key to leveraging this workflow effectively.

### When do I...

*   **...move from vision to planning?**
    *   After you have run `refine-architecture` and are confident that the vision is solid and the major risks have been considered. The output of this command is the green light to proceed with `init-project`.

*   **...run an audit?**
    *   After merging a few major features.
    *   When the codebase starts to feel "messy" or difficult to navigate.
    *   Before a major release, as a final quality check.
    *   When you first join or return to a project.

*   **...consider a re-architecture?**
    *   When implementing new features feels harder than it should. This is often a sign of architectural drift.
    *   When you realize the product you've built no longer matches the original `vision.md`.
    *   When a core dependency needs to be replaced, forcing a significant change in how the system works.

*   **...deprecate a feature?**
    *   When analytics show the feature is no longer being used.
    *   When a new, better feature has been built to replace it.
    *   When maintaining the feature is causing more problems than the value it provides.