# One-Shot AI Prompt for Yazi Plugin Manager Dashboard in Bash

Generate a **fully-featured Bash script** for managing Yazi plugins with the following requirements:

1. **Plugin Management**:
   - Support `install`, `update`, `remove`, `list`, and `status`.
   - Use a predefined Bash array of plugins, and optionally fetch all plugins (`--all`).
   - Skip already installed plugins when installing.

2. **Dashboard Features**:
   - Live updating dashboard in the terminal.
   - Each plugin line shows:
     - Spinner (`|/-\`) while pending.
     - Colored icon for completed tasks: `✔` (installed, green), `⟳` (updated, blue), `✖` (removed, red), `➡` (skipped, yellow), `✘` (missing, red).
   - Global progress bar with percentage completion and ETA in MM:SS.
   - ANSI escape sequences rendered correctly with `printf '%b'`.
   - Use `tput sc`/`tput rc` to avoid flicker.

3. **Concurrency**:
   - Run plugin operations in parallel with a configurable maximum concurrency.
   - Ensure proper synchronization and update dashboard dynamically.

4. **Summary**:
   - Display a final summary with colored counts for installed, updated, removed, skipped, and missing plugins.
   - Optional JSON output with `--json`.

5. **Technical Details**:
   - Use Bash 4+.
   - Use standard Unix tools only (`printf`, `seq`, `tput`, `mktemp`, etc.).
   - Handle empty plugin directories and avoid `printf: -%: invalid option`.
   - ETA calculation should update dynamically based on completed plugins and elapsed time.
   - Script must be self-contained and ready to run.

6. **Command-Line Options**:
   - `--update`, `--remove`, `--list`, `--status`, `--all`, `--json`.

7. **Output Requirements**:
   - Clean, single dashboard updating in-place.
   - Spinners animate for pending tasks.
   - Colors display properly.
   - Progress bar and ETA update live.

**Output**: A single Bash script implementing all the above features, fully commented for clarity, ready to run in a standard terminal with Yazi installed.

