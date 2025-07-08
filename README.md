# Architect Agent Project

This project contains a system for collaborating with an AI assistant to act as a **System Architect**. Its purpose is to help you transform a high-level project idea into a concrete, actionable set of `INITIAL.md` files that are ready for implementation with this workflow: https://github.com/coleam00/context-engineering-intro

## 🚀 Workflow

### 1. Define Your Vision
- Copy the `prompts/VISION_TEMPLATE.md` to a new file (e.g., `my_project_vision.md`).
- Fill out the sections to the best of your ability. It's okay to have "Open Questions"—the agent is designed to help you answer them.

### 2. Generate the Project Plan
- Run the custom command in your AI assistant (e.g., Claude Code):
  ```bash
  /generate_project_plan my_project_vision.md

## 🔄 Revision Workflow

When requirements change, you don't need to start over. Use the revision command to intelligently update your plan.

### 1. Initiate a Revision
- Run the `revise_project_plan` command with the path to your existing plan and a description of the change.
  ```bash
  /revise_project_plan output/my-project/PROJECT_PLAN.md "Change the database from PostgreSQL to ChromaDB for semantic search capabilities."
