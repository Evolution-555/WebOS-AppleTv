# GitHub Actions Setup Complete

I've set up GitHub Actions to automatically build the IPK on Ubuntu runners, solving the Windows build issue.

## What's Been Set Up

### 1. Build Workflow (`.github/workflows/build.yml`)
- **Triggers:** On push to `main` branch
- **What it does:**
  - Runs on Ubuntu (solves Windows encoding issues)
  - Installs dependencies
  - Runs checks
  - Builds the IPK
  - Uploads artifacts (available for 30 days)

### 2. Release Workflow (`.github/workflows/release.yml`)
- **Triggers:** On tag push (e.g., `v1.0.0`) or manual run
- **What it does:**
  - Runs on Ubuntu
  - Builds the IPK
  - Creates GitHub release with IPK files
  - Generates release notes

## What Just Happened

1. ✅ Created and pushed the GitHub Actions workflows
2. ✅ Fixed workflow issues (removed unnecessary permissions)
3. ✅ Created and pushed tag `v1.0.0`
4. 🔄 **Release workflow is now running** (triggered by the tag)

## Check the Build Status

Go to: https://github.com/Evolution-555/WebOS-AppleTv/actions

You should see the "Release" workflow running. Once it completes:
- A GitHub release will be created at: https://github.com/Evolution-555/WebOS-AppleTv/releases/tag/v1.0.0
- The IPK file will be attached to the release
- The `apps.json` will be available for Homebrew Channel

## How to Use

### Option 1: Download from GitHub Release (Recommended)
1. Wait for the workflow to complete (~5-10 minutes)
2. Go to: https://github.com/Evolution-555/WebOS-AppleTv/releases
3. Download `com.cleanyourtv.manager_<version>_all.ipk`
4. Install on your TV via SSH or Homebrew Channel

### Option 2: Add to Homebrew Channel
Once the release is complete, add this repository to Homebrew Channel:
```
https://github.com/Evolution-555/WebOS-AppleTv/releases/latest/download/apps.json
```

### Option 3: Manual Build (Artifacts)
If you want to test without a release:
1. Go to: https://github.com/Evolution-555/WebOS-AppleTv/actions
2. Click on the latest "Build" workflow run
3. Download artifacts from the bottom of the page

## Future Releases

To create a new release:

```bash
# Make your changes
git add .
git commit -m "Your changes"
git push origin main

# Create a new tag
git tag v1.0.1
git push origin v1.0.1
```

The tag push will automatically trigger the release workflow.

## Manual Build Without Release

If you just want to build without creating a release:

1. Go to: https://github.com/Evolution-555/WebOS-AppleTv/actions
2. Click "Build" workflow
3. Click "Run workflow"
4. Select branch and click "Run"
5. Download artifacts when complete

## Troubleshooting

### Workflow Failed
- Check the workflow logs at: https://github.com/Evolution-555/WebOS-AppleTv/actions
- Look for error messages in the logs
- Common issues: test failures, missing dependencies

### No Release Created
- Make sure the tag was pushed: `git push origin v1.0.0`
- Check the release workflow status
- The workflow must complete successfully for the release to be created

### Can't Find IPK
- Check the "Artifacts" section of the workflow run
- Or check the "Releases" section of the repository
- Make sure the workflow completed successfully

## Current Status

- ✅ Workflows set up
- ✅ Workflows fixed (removed unnecessary permissions)
- ✅ Tag v1.0.0 pushed
- 🔄 Release workflow running (check Actions tab)
- ⏳ Waiting for release to be created

Monitor the progress at: https://github.com/Evolution-555/WebOS-AppleTv/actions
