# Sub-PRP: [Sub-Feature Title]

**Epic:** [Link to parent epic.md](../epic.md)
**Status:** `Pending` | `In Progress` | `Blocked` | `Done`

## 1. Goal

A clear and concise description of what this specific task will accomplish. This should be a single, verifiable outcome.

**Success Criteria:**
- [ ] Code is implemented and passes all new unit tests.
- [ ] All validation steps (linting, type-checking) pass.
- [ ] The implementation is successfully integrated with the `main` branch.

---

## 2. Technical Plan

A detailed, step-by-step implementation plan for this specific task.

**Files to be Created/Modified:**
- `src/module/new_file.py`
- `tests/module/test_new_file.py`

**Implementation Details:**
*(Provide pseudocode, data models, and specific logic required for this task. This section replaces the verbose "Implementation Blueprint" of the old template.)*

```python
# src/module/new_file.py
class NewService:
    def __init__(self, db_session):
        self.db = db_session

    def process_data(self, data):
        # CRITICAL: Validate input data using the shared validator
        validated_data = self._validate(data)
        # ... core logic ...
        return result
```

---

## 3. All Needed Context

This section is critical for the AI. Provide only the context **absolutely necessary** for this specific task.

**Relevant Code Snippets:**
*(Include small, relevant snippets from existing files that the AI needs to be aware of.)*

**Key Patterns to Follow:**
- **Error Handling:** Follow the pattern in `src/shared/errors.py`.
- **Configuration:** Add new configs to `config/settings.py` using the existing format.

---

## 4. Validation Loop

Provide the exact commands to run to validate the implementation of **this Sub-PRP only**.

**Level 1: Syntax & Style**
```bash
ruff check src/module/new_file.py --fix
black src/module/new_file.py
```

**Level 2: Unit Tests**
```bash
pytest tests/module/test_new_file.py