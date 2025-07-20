# Project Building & Style Guide

This document outlines the specific coding standards, testing methodologies, and documentation practices for this project. All AI-generated code must adhere to these guidelines.

### 🧱 Code Structure & Modularity
- **File Size Limit:** Never create a file longer than 500 lines of code. If a file approaches this limit, refactor by splitting it into smaller, more focused modules.
- **Module Organization:** Organize code into clearly separated modules, grouped by feature or responsibility.
- **Imports:** Use clear, consistent, and absolute imports.
- **Environment Variables:** Use `python-dotenv` and `load_dotenv()` for managing environment variables. Do not commit `.env` files.

### 🧪 Testing & Reliability
- **Test Creation:** Always create Pytest unit tests for new features (functions, classes, routes, etc.).
- **Test Maintenance:** After updating any logic, check whether existing unit tests need to be updated. If so, perform the update.
- **Test Location:** Tests must live in a `/tests` folder that mirrors the main application structure.
- **Test Coverage:** Each feature should have at least:
    - 1 test for the expected "happy path" use case.
    - 1 test for a known edge case.
    * 1 test for an expected failure case (e.g., invalid input).

### 📎 Style & Conventions
- **Primary Language:** Python.
- **Formatting:** Follow PEP8 standards. All code should be formatted with `black`.
- **Type Hinting:** Use type hints for all function signatures and variables where appropriate.
- **Data Validation:** Use `pydantic` for all data validation and settings management.
- **API & ORM:** Use `FastAPI` for APIs and `SQLAlchemy` or `SQLModel` for ORM if applicable.

### 📚 Documentation & Explainability
- **Docstrings:** Write docstrings for every function using the Google style format.
- **Code Comments:** Comment non-obvious code. When writing complex logic, add an inline `# Reason:` comment explaining the *why*, not just the *what*.
- **README Updates:** The `README.md` should be updated when new features are added, dependencies change, or setup steps are modified.