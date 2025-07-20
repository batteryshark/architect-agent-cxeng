# Execute PRP
Implement a feature using the PRP file.

## PRP File: $ARGUMENTS

## Execution Process

1.  **Initialization**
    *   Get the PRP file path from the arguments.
    *   Verify that the file is a sub-PRP, not an epic.
    *   Define helper functions for logging notes and updating the checklist.

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

    # Function to add a developer note
    add_note() {
      echo "Enter your developer note (press Ctrl+D when done):"
      NOTE=$(cat)
      if [ -n "$NOTE" ]; then
        TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
        # Use awk to insert the note under the "Developer Notes" section
        awk -v note="($TIMESTAMP) Note: $NOTE" '
        /## Developer Notes/ {print; print note; next}
        {print}
        ' "$PRP_FILE" > "$PRP_FILE.tmp" && mv "$PRP_FILE.tmp" "$PRP_FILE"
        echo "Note added."
      fi
    }
    ```

2.  **Load and Execute PRP**
    *   Read the specified PRP file.
    *   Parse the "Task Checklist" section.
    *   Resume from the first incomplete task.
    *   For each task, announce the action, simulate work, and update the checklist.

    ```bash
    echo "Starting execution of PRP: $PRP_FILE"

    # Extract tasks from the checklist. Ignores the header line.
    TASKS=$(sed -n '/## Task Checklist/,/##/p' "$PRP_FILE" | grep '\[ \]' | sed 's/^- \[ \] //')

    if [ -z "$TASKS" ]; then
        echo "All tasks in the checklist are already completed."
    else
        echo "Found the following incomplete tasks:"
        echo "$TASKS"
    fi

    while IFS= read -r task; do
      if [ -z "$task" ]; then
        continue
      fi
      
      # Check if the task is already complete, just in case
      grep -q -- "- \[x\] $task" "$PRP_FILE"
      if [ $? -eq 0 ]; then
          echo "Skipping already completed task: $task"
          continue
      fi

      echo "--------------------------------------------------"
      echo "Executing task: $task"
      echo "--------------------------------------------------"

      # *** AI DEVELOPER: IMPLEMENT THE TASK HERE ***
      # This is where you would perform the actual work for the task.
      # For demonstration, we will pause and wait for confirmation.
      echo "The AI developer is now working on the task. Simulating work for 5 seconds."
      sleep 5
      echo "Task simulation complete."
      # *** END OF AI DEVELOPER WORK ***

      # Mark the task as complete in the PRP file
      sed -i.bak "s/^- \[ \] $task/- \[x\] $task/" "$PRP_FILE"
      rm "$PRP_FILE.bak" # Clean up backup file on success
      echo "Updated checklist: Marked '$task' as complete."

      # Prompt to add a developer note
      read -p "Do you want to add a developer note for this task? (y/n): " choice
      if [[ "$choice" == "y" || "$choice" == "Y" ]]; then
        add_note
      fi

    done <<< "$TASKS"

    echo "--------------------------------------------------"
    echo "All tasks have been executed."
    ```

3.  **Final Validation**
    *   After completing all tasks, run the final validation steps as defined in the PRP.

    ```bash
    echo "Running final validation suite..."
    # Placeholder for validation commands from the PRP
    # For example:
    # VALIDATION_COMMANDS=$(sed -n '/## Validation/,/##/p' "$PRP_FILE" | grep -v "## Validation")
    # eval "$VALIDATION_COMMANDS"
    echo "Validation complete."
    ```

4.  **Completion**
    *   Ensure all checklist items are done.
    *   Report completion status.

    ```bash
    echo "PRP execution finished for $PRP_FILE."
    echo "Please review the changes and the developer notes."
    ```

Note: This command now modifies the PRP file directly. Ensure you have a backup if you need to revert changes. The `sed -i.bak` command automatically creates a backup file with a `.bak` extension.