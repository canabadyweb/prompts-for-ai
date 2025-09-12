## Zero-Friction Dotfiles Management Across Multiple Machines Using Only Git, with Secret Scanning and Sync

---

### Core Requirements

1. **Bare Git repository**
   - Store all dotfiles in a bare repo in `$HOME/.dotfiles`.
   - Track multiple configuration files like `.vimrc`, `.zshrc`, `.bashrc`, `.gitconfig`, `.config/nvim/init.vim`.

2. **CLI Helper**
   - A helper script called `dotfiles` with commands:
     - `scan` → Runs a secret scanner.
     - `sync` → Pull latest dotfiles and apply symlinks across machines.
     - `push`, `add`, `commit`, `status` → Standard Git operations on the dotfiles repo.

3. **Secret Scanning**
   - A script `scan-secrets.sh` that:
     - Supports **report mode** (dry-run) and **enforce mode** (blocks push if issues found).
     - Supports **emergency bypass** via `ALLOW_UNSAFE_PUSH=1` (local only, ignored in CI).
     - Configurable via `.dotfiles-scanrc`:
       - `block-paths` → Files or directories not allowed.
       - `warn-paths` → Files or directories that are risky.
       - `block-content` → Regex patterns that block commits.
       - `warn-content` → Regex patterns that warn only.

4. **Pre-Push Hook**
   - Calls the secret scanner automatically before each push.

5. **Sync Command**
   - Pulls the latest changes from the repo.
   - Applies symlinks for tracked configs into `$HOME`.
   - Backs up any overwritten files to `~/.dotfiles-backup`.

6. **Bootstrap Installer**
   - Script `install-dotfiles.sh` to set up a new machine.
   - Clones the bare repo.
   - Checks out files safely (backing up any existing ones).
   - Installs pre-push hook.
   - Installs CLI helper.

7. **CI Compatibility**
   - Secret scanning should run in CI even if local bypass is set.
   - Enforce mode should block pushes in CI if violations are found.

8. **Repository Structure**
```
dotfiles/
├── install-dotfiles.sh
├── dotfiles-scanrc
├── scripts/scan-secrets.sh
├── hooks/pre-push
├── bin/dotfiles
├── tracked-configs/
│   ├── .vimrc
│   ├── .zshrc
│   ├── .bashrc
│   ├── .gitconfig
│   └── .config/nvim/init.vim
├── .gitignore
└── README.md
```

9. **Usage Examples**
```bash
# Bootstrap on new machine
curl -fsSL https://raw.githubusercontent.com/<username>/dotfiles/main/install-dotfiles.sh | bash

# Sync dotfiles
dotfiles sync

# Run secret scan (report mode)
dotfiles scan

# Run secret scan (enforce mode)
dotfiles scan --enforce

# Push changes
dotfiles add ~/.vimrc
dotfiles commit -m "Update vimrc"
dotfiles push

# Emergency bypass (local only)
ALLOW_UNSAFE_PUSH=1 dotfiles push
```

10. **Features**
- Bare Git repository for dotfiles.
- Local pre-push hook + CI-compatible secret scan.
- Report mode + enforce mode + emergency bypass.
- Cross-machine sync using `dotfiles sync`.
- Automatic backup of overwritten files.
- Centralized `.dotfiles-scanrc` for secret rules.
- CLI helper for all common dotfiles operations.

---

### Request

Please generate:

1. **Complete repo skeleton** with all scripts and hooks populated.
2. **Full scripts for:**
   - `install-dotfiles.sh` (bootstrap)
   - `scripts/scan-secrets.sh` (secret scan)
   - `bin/dotfiles` (CLI helper)
   - `hooks/pre-push` (hook to call secret scan)
3. **Default `.dotfiles-scanrc`** with sample block/warning rules.
4. **Sample tracked config files** for `.vimrc`, `.zshrc`, `.bashrc`, `.gitconfig`, and `nvim/init.vim`.
5. **Instructions to bootstrap on a new machine**, sync, scan, and push.
6. **Ensure CI compatibility** and local bypass is ignored in CI.
7. Ready-to-clone **GitHub repo template structure**.

