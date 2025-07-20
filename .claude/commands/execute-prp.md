# Execute PRP

Implement a feature using the PRP file.

## PRP File: $ARGUMENTS

## Execution Process

1.  **Analyze PRP Type**
    *   Get the PRP file path from the arguments.
    *   Check if the file is an `epic.md` file or a `sub-prp.md` file.

    ```bash
    # Get the PRP file path from the arguments
    PRP_FILE="$ARGUMENTS"

    # Get the directory of the PRP file
    PRP_DIR=$(dirname "$PRP_FILE")

    # Check if the file is an epic.md file
    if [[ $(basename "$PRP_FILE") == "epic.md" ]]; then
      echo "The 'execute-prp' command is intended for implementing sub-PRPs, not epics. Please run this command on one of the linked sub-PRPs."
      
      # Check if the sub-prps directory exists
      if [ -d "$PRP_DIR/sub-prps" ]; then
        echo "Available sub-PRPs:"
        ls -1 "$PRP_DIR/sub-prps" | sed 's/^/- /'
      else
        echo "No sub-PRPs found for this epic."
      fi
      exit 0
    fi
    ```

2.  **Load PRP**
    *   Read the specified PRP file.
    *   Understand all context and requirements.
    *   Follow all instructions in the PRP and extend the research if needed.
    *   Ensure you have all needed context to implement the PRP fully.
    *   Do more web searches and codebase exploration as needed.

3.  **ULTRATHINK**
    *   Think hard before you execute the plan. Create a comprehensive plan addressing all requirements.
    *   Break down complex tasks into smaller, manageable steps using your todos tools.
    *   Use the TodoWrite tool to create and track your implementation plan.
    *   Identify implementation patterns from existing code to follow.

4.  **Execute the plan**
    *   Execute the PRP.
    *   Implement all the code.

5.  **Validate**
    *   Run each validation command.
    *   Fix any failures.
    *   Re-run until all pass.

6.  **Complete**
    *   Ensure all checklist items done.
    *   Run final validation suite.
    *   Report completion status.
    *   Read the PRP again to ensure you have implemented everything.

7.  **Reference the PRP**
    *   You can always reference the PRP again if needed.

Note: If validation fails, use error patterns in PRP to fix and retry.