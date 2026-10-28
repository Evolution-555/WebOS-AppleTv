# Setup GitHub Repository for AppleTv CleanYourTV

This guide will help you set up your own GitHub repository for the AppleTv edition of CleanYourTV.

## Step 1: Create a New GitHub Repository

1. Go to https://github.com/new
2. Repository name: `appletv-cleanyourtv`
3. Description: "CleanYourTV for LG webOS with AppleTv theme as default"
4. Make it **Public** (so Homebrew Channel can access it)
5. **DO NOT** initialize with README, .gitignore, or license (we already have these)
6. Click "Create repository"

## Step 2: Add Your Repository as Remote

```bash
cd "C:\Users\Evan_Conlon\sdd-workspace\Clean you tv test\appletv-cleanyourtv"
git remote add origin https://github.com/YOUR_USERNAME/appletv-cleanyourtv.git
```

Replace `YOUR_USERNAME` with your actual GitHub username.

## Step 3: Push to Your Repository

```bash
git branch -M main
git push -u origin main
```

## Step 4: Update apps.json for Homebrew Channel

The Homebrew Channel needs an `apps.json` file. Create one in the repository root:

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

Replace `YOUR_USERNAME` with your GitHub username.

## Step 5: Build the IPK

```bash
cd "C:\Users\Evan_Conlon\sdd-workspace\Clean you tv test\appletv-cleanyourtv"
python3 ipk/build.py
```

This will create the IPK file in the `dist/` directory.

## Step 6: Create a GitHub Release

1. Go to your repository on GitHub
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
   - 4K optimized
   - Sound design integration

   ### Installation
   Add this repository to Homebrew Channel:
   https://github.com/YOUR_USERNAME/appletv-cleanyourtv/releases/latest/download/apps.json
   ```
6. Upload the IPK file from `dist/` directory
7. Click "Publish release"

## Step 7: Test Homebrew Channel Installation

On your TV:
1. Open Homebrew Channel
2. Go to Settings (gear icon)
3. Select "Add repository"
4. Enter:
   ```
   https://github.com/YOUR_USERNAME/appletv-cleanyourtv/releases/latest/download/apps.json
   ```
5. "CleanYourTV AppleTv" should appear in the app list
6. Select it and choose "Install"

## Step 8: Future Updates

When you want to update the app:

1. Make changes to the code
2. Build the IPK: `python3 ipk/build.py`
3. Commit and push changes
4. Create a new GitHub release with the new IPK
5. Users will see the update in Homebrew Channel

## Important Notes

- **Keep upstream synced**: Periodically run `git fetch upstream && git merge upstream/main` to get updates from the original CleanYourTV
- **Theme updates**: If you update the AppleTv theme, copy the new files to `themes/appletv/`
- **Default theme**: The `config.example.json` sets `"theme": "appletv"` as default
- **All themes included**: Users can still switch to other themes in the manager app

## Troubleshooting

### Homebrew Channel can't find the repository
- Check that the repository is public
- Verify the apps.json URL is correct
- Check that the IPK file is attached to the release

### Theme not showing as default
- Ensure `config.example.json` has `"theme": "appletv"`
- The theme files must be in `themes/appletv/`
- Check that `themes/index.json` includes the appletv entry

### Build fails
- Ensure Python 3 is installed
- Check that all dependencies are in place
- Run `sh tools/check.sh` to verify everything is working
