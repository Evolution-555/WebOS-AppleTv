# Next Steps to Release on Homebrew Channel

Your AppleTv edition of CleanYourTV is now ready! Here's what you need to do to release it on the Homebrew Channel.

## ✅ What's Been Done

1. **Cloned CleanYourTV** - Forked the original repository
2. **Added AppleTv theme** - Copied theme files to `themes/appletv/`
3. **Set as default** - Modified `config.example.json` to use AppleTv by default
4. **Updated theme index** - Added AppleTv to `themes/index.json` (first in list)
5. **Updated README** - Changed to reflect AppleTv edition
6. **Created setup guide** - `SETUP-GITHUB.md` with detailed instructions
7. **Created apps.json** - Homebrew Channel manifest file
8. **Committed changes** - All changes are committed locally

## 📋 What You Need to Do

### Step 1: Create Your GitHub Repository

1. Go to https://github.com/new
2. Repository name: `appletv-cleanyourtv`
3. Description: "CleanYourTV for LG webOS with AppleTv theme as default"
4. Make it **Public** (required for Homebrew Channel)
5. **DO NOT** initialize with README, .gitignore, or license
6. Click "Create repository"

### Step 2: Connect Your Repository

```bash
cd "C:\Users\Evan_Conlon\sdd-workspace\Clean you tv test\appletv-cleanyourtv"
git remote add origin https://github.com/YOUR_USERNAME/appletv-cleanyourtv.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` with your actual GitHub username.

### Step 3: Update apps.json

Edit `apps.json` and replace `Evolution-555` with your GitHub username:

```json
{
  "apps": [
    {
      "id": "com.evolution555.cleanyourtv",
      "title": "CleanYourTV AppleTv",
      "version": "1.0.0",
      "icon": "https://github.com/YOUR_USERNAME/appletv-cleanyourtv/raw/main/assets/icon.svg",
      "type": "web",
      "main": "https://github.com/YOUR_USERNAME/appletv-cleanyourtv/releases/latest/download/com.evolution555.cleanyourtv.ipk",
      "requiredMemory": 256
    }
  ]
}
```

Commit this change:
```bash
git add apps.json
git commit -m "Update apps.json with correct username"
git push
```

### Step 4: Build the IPK

```bash
cd "C:\Users\Evan_Conlon\sdd-workspace\Clean you tv test\appletv-cleanyourtv"
python3 ipk/build.py
```

This creates the IPK file in the `dist/` directory.

### Step 5: Create GitHub Release

1. Go to your new repository on GitHub
2. Click "Releases" → "Create a new release"
3. Tag version: `v1.0.0`
4. Release title: "AppleTv Edition v1.0.0"
5. Description:
   ```
   ## AppleTv Edition v1.0.0

   CleanYourTV with AppleTv theme as default.

   ### Features
   - Authentic Apple TV design
   - Glassmorphism effects
   - Spring animations
   - 4K optimized (3840x2160)
   - Sound design integration
   - San Francisco typography

   ### Installation
   Add this repository to Homebrew Channel:
   https://github.com/YOUR_USERNAME/appletv-cleanyourtv/releases/latest/download/apps.json
   ```
6. Upload the IPK file from `dist/` directory (drag and drop)
7. Click "Publish release"

### Step 6: Test Installation

On your TV:
1. Open Homebrew Channel
2. Go to Settings (gear icon at top)
3. Select "Add repository"
4. Enter:
   ```
   https://github.com/YOUR_USERNAME/appletv-cleanyourtv/releases/latest/download/apps.json
   ```
5. "CleanYourTV AppleTv" should appear in the app list
6. Select it and choose "Install"
7. Open the app and set it up - it should use AppleTv theme by default

## 🔄 Future Updates

When you want to update the app:

1. Make changes to the code
2. Build the IPK: `python3 ipk/build.py`
3. Commit and push changes
4. Create a new GitHub release with the new IPK
5. Users will see the update in Homebrew Channel

## 📝 Optional: Add Preview Image

To make the theme look better in the theme selector:

1. Take a screenshot of the AppleTv theme in action on your TV
2. Resize to approximately 800x450 pixels
3. Save as `themes/appletv/preview.jpg`
4. Commit and push:
   ```bash
   git add themes/appletv/preview.jpg
   git commit -m "Add AppleTv theme preview image"
   git push
   ```

## 🔄 Keeping Up with Original CleanYourTV

To get updates from the original CleanYourTV:

```bash
cd "C:\Users\Evan_Conlon\sdd-workspace\Clean you tv test\appletv-cleanyourtv"
git fetch upstream
git merge upstream/dev
```

Resolve any conflicts, then push to your repository.

## 🎯 Summary

Your AppleTv edition is ready to release! Once you complete the steps above, users will be able to:

- Add your repository to Homebrew Channel
- Install CleanYourTV with AppleTv theme pre-configured
- Switch to other themes if they prefer
- Get updates through Homebrew Channel

The theme will be the default, but all other CleanYourTV features and themes remain available.

## 📚 Documentation

- **SETUP-GITHUB.md** - Detailed setup instructions
- **README.md** - Updated for AppleTv edition
- **Original CleanYourTV docs** - All original documentation is included
- **WebOS-AppleTv/SOUND-DESIGN.md** - Sound design guide (in the theme source repo)

## 🆘 Need Help?

- CleanYourTV Discord: https://discord.gg/9hHAmCfqB
- CleanYourTV GitHub: https://github.com/lasharor/cleanyourtv-WebOS
- CleanYourTV Documentation: https://lasharor.github.io/cleanyourtv-WebOS/
