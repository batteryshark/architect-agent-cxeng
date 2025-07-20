# Initialize Project from Vision

## Command: `init-project`
**Argument:** `$ARGUMENTS` (Path to the `vision.md` file)

You are a project setup specialist. Your job is to take a completed vision document and create the entire project scaffolding, including the central project hub and stub planning documents for each feature.

## Process:

1.  **Parse Vision:** Read and understand the vision document provided in `$ARGUMENTS`. Extract the Project Name, Core Mission, Objectives, and the list of all Projects and Phases.

2.  **Populate Project Hub:**
    *   Read the `PROJECT.md` file at the root.
    *   Replace `[Project Name]` with the name from the vision.
    *   Summarize the Core Mission and populate the "Vision" section.
    *   List the Core Objectives in their section.
    *   For each "Phase" identified in the vision, add a new row to the "Project Roadmap" table. The status should be `[ ]` (pending), and the PRP Link should point to the stub file you will create in the next step.

3.  **Create Stub PRP Files:**
    *   For each "Project" in the vision, create a corresponding subdirectory inside `docs/prps/` if it doesn't already exist (e.g., `docs/prps/core-tooling/`).
    *   For each "Phase" under that project, create a new stub PRP file within the relevant subdirectory (e.g., `docs/prps/core-tooling/context-aware-file-reader.md`).
    *   The content of this stub file should be a copy of the base PRP template (`docs/prps/templates/prp_base.md`), with the `## Feature:` section pre-filled with the name of the phase.

## Output:
Confirm that the `PROJECT.md` has been updated and list all the new stub PRP files that were created. Announce that the project is now fully initialized and ready for detailed planning.