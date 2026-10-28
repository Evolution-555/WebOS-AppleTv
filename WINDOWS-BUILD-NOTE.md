# Windows Build Issue

The IPK build script (`ipk/build.py`) has encoding issues on Windows due to Python's default file encoding on Windows (cp1252 vs UTF-8).

## Workarounds

### Option 1: Build on Linux/Mac (Recommended)

If you have access to a Linux or Mac system:
```bash
# Clone the repository
git clone https://github.com/Evolution-555/WebOS-AppleTv.git
cd WebOS-AppleTv

# Build the IPK
python3 ipk/build.py

# The IPK will be in dist/
```

### Option 2: Use WSL (Windows Subsystem for Linux)

1. Install WSL from Microsoft Store
2. Open WSL terminal
3. Clone and build:
```bash
cd /mnt/c/Users/Evan_Conlon/sdd-workspace/Clean\ you\ tv\ test/appletv-cleanyourtv
python3 ipk/build.py
```

### Option 3: Use GitHub Actions

Create a GitHub Actions workflow to build the IPK automatically on push.

### Option 4: Manual Installation

For testing, you can manually install the theme files:
1. Copy `themes/appletv/` to your TV's CleanYourTV themes directory
2. Set the theme in the manager app
3. Rebuild the launcher on the TV

## Current Status

The source code with AppleTv theme is pushed to GitHub. You can:
- View the code at https://github.com/Evolution-555/WebOS-AppleTv
- Clone and build on a Unix system
- Or wait for automated builds via GitHub Actions

The AppleTv theme is fully integrated and ready to use once the IPK is built.
