# Prompt for Generating a Yazi Plugin Manager Dashboard Script in Bash

## Objective
Create a **fully-featured Bash script** to manage Yazi plugins with the following capabilities:

1. **Plugin Operations**:
   - Install, update, remove, list, and check status of plugins.
   - Support a predefined array of plugins and also allow fetching all plugins dynamically (`--all`).
   - Skip plugins that are already installed when installing.

2. **Concurrency**:
   - Run multiple plugin operations in parallel with a configurable maximum concurrency level.
   - Ensure proper synchronization so output does not mix or break the progress display.

3. **Interactive Dashboard**:
   - Show a live, updating dashboard of plugin installation statuses.
   - Each plugin line should display a **spinner** while pending, or a colored icon for completed statuses:
     - `✔` for installed
     - `⟳` for updated
     - `✖` for removed
     - `➡` for skipped
     - `✘` for missing
   - Color coding using ANSI escape sequences:
     - Green: Installed
     - Blue: Updated
     - Red: Removed / Missing
     - Yellow: Skipped
     - Cyan: Pending

4. **Progress Bar**:
   - Display a **global progress bar** of total plugin operations.
   - Show **percentage completion** and **ETA in MM:SS format**.

5. **Robust ANSI Color Handling**:
   - All ANSI codes must render correctly using `printf` with `%b`.
   - Avoid printing literal escape sequences.

6. **Error Handling**:
   - Prevent `printf: -%: invalid option` by ensuring numeric variables and properly formatted format strings.
   - Handle empty plugin directories gracefully.

7. **Output Summary**:
   - Display a final summary with colored counts for each status (installed, updated, removed, skipped, missing).
   - Optionally, provide JSON output via a `--json` flag with detailed plugin statuses and a summary.

8. **Command-Line Options**:
   - `--update`: update plugins.
   - `--remove`: remove plugins.
   - `--list`: list all plugins.
   - `--status`: show current status of installed plugins.
   - `--all`: fetch and operate on all available plugins.
   - `--json`: output summary in JSON format.

9. **Technical Requirements**:
   - Use `tput sc` and `tput rc` for cursor save/restore to prevent screen flicker.
   - Use `seq` and `printf` for dynamic progress bar generation.
   - Use a temporary file to track plugin statuses.
   - Ensure compatibility with **bash 4+** and standard Unix tools.
   - Script should be **self-contained**, requiring no external dependencies other than `ya` (Yazi package manager).

10. **Expected Behavior**:
    - When running, the terminal should show **one clean, updating dashboard** rather than duplicating plugin lines.
    - Spinners should animate until the plugin task completes.
    - ETA should update in real time.
    - Final summary should be displayed with colors or JSON.

---

### Deliverable
Provide a **single Bash script** implementing all the features above, fully commented for readability, ready to run in a standard Bash terminal.

Make sure all ANSI codes, progress bar, spinner animation, concurrency handling, and ETA calculation are working correctly.

---

### Notes
- Each plugin in the array should have a `.yazi` directory in `$XDG_CONFIG_HOME/yazi/plugins`.
- Assume `ya pkg add|upgrade|remove` commands are available and work silently.
- Ensure the script works with **both small and large numbers of plugins** without breaking the dashboard.
- ETA should be recalculated dynamically based on completed plugins and elapsed time.

