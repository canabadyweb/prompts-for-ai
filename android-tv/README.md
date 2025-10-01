# Android TV CLI Remote Control Prompt Instructions

**Objective:**
Create a comprehensive CLI tool for controlling Android TV over Wi-Fi using ADB, supporting navigation, media control, text input, app launching, app discovery, fuzzy search, and favorites.

**Details to include in the prompt:**

1. **Setup Instructions**
   - Mention enabling Developer Options and ADB Debugging on Android TV.
   - Connecting to Android TV over Wi-Fi using `adb connect <IP>:<port>`.
   - Optional: installing `fzf` for interactive app selection.

2. **Commands to Implement**
   - **Navigation:** home, back, menu, up, down, left, right, ok/enter.
   - **Volume:** volup, voldown, mute.
   - **Media:** play, pause, playpause, stop, next, prev, ff, rw.
   - **TV-specific:** guide, info, input, cc, chup, chdown.
   - **Text Input:** allow typing arbitrary text.
   - **App Launching:** launch by name or package; include popular apps (YouTube, Netflix, Prime, Disney+, Plex, Kodi, VLC, Settings).
   - **App Discovery:** list installed apps by package name.
   - **Apps with Friendly Names:** display app names with packages; support search queries and interactive fzf selection.
   - **Favorites:** add, remove, list, and launch favorite apps.

3. **Features to Highlight**
   - Fuzzy search with `fzf` if available.
   - Quick search & launch via text query.
   - Favorites system with easy commands.

4. **Usage Examples**
   - Demonstrate navigation, media control, text input.
   - Show app discovery, fuzzy search, search queries.
   - Show adding, listing, launching, and removing favorites.

5. **Output Expectations**
   - Clearly indicate actions (e.g., "Launching YouTube → com.google.android.youtube.tv").
   - Show error messages for missing apps or favorites.

6. **Notes**
   - Ensure instructions mention all features should work over Wi-Fi via ADB.
   - Keep the prompt modular so it can be used to regenerate or extend the CLI tool anytime.

**Example Prompt Text:**

"Create a comprehensive CLI tool to control Android TV over Wi-Fi using ADB. Include navigation, media controls, text input, app launching, app discovery, fuzzy search via fzf, search queries, and a favorites system. Show usage examples and output expectations."
