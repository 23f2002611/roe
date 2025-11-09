# Multi-Platform Matrix Build with GitHub Actions

## Contact Information
**Email**: 23f2002611@ds.study.iitm.ac.in

## Overview
This repository demonstrates a comprehensive GitHub Actions matrix build strategy that:
- Builds across multiple operating systems (Ubuntu, macOS, Windows)
- Tests multiple Node.js versions (16, 18, 20)
- Generates unique artifacts for each matrix combination
- Implements parallel execution for efficient CI/CD

## Matrix Configuration

### Build Matrix
The workflow creates **7 parallel jobs** with the following combinations:

| OS | Node Version | Job Count |
|---|---|---|
| Ubuntu | 16, 18, 20 | 3 |
| macOS | 18, 20 | 2 |
| Windows | 18, 20 | 2 |

**Total Jobs**: 7 parallel builds

## Workflow Features

### ✅ Required Components
- [x] Matrix strategy with 3+ variants
- [x] Parallel execution across all variants
- [x] Unique artifacts for each build (`build-5976bde-<variant>`)
- [x] Step identifier: `matrix-5976bde`
- [x] Non-empty artifact content
- [x] Email address in README

### 🚀 Additional Features
1. **Build Metadata**: JSON file with build information
2. **Sample Application**: Express.js app for each platform
3. **Build Summary**: GitHub Actions summary for each job
4. **Artifact Collection**: Post-build job that collects all artifacts
5. **Comprehensive Report**: Combined report of all builds

## Artifacts Generated

Each matrix job generates an artifact with the naming pattern:
```
build-5976bde-<os>-node<version>
```

### Artifact Contents
Each artifact includes:
- `build.txt` - Build information and metadata
- `build-metadata.json` - Structured build data
- `app.js` - Sample Express.js application
- `package.json` - Node.js dependencies

### Example Artifacts
- `build-5976bde-ubuntu-latest-node18`
- `build-5976bde-macos-latest-node20`
- `build-5976bde-windows-latest-node18`
- `build-5976bde-ubuntu-latest-node16`
- ... (7 total artifacts)

Plus one final report:
- `build-5976bde-report`

## Workflow Triggers

The workflow runs on:
- Push to `main` or `master` branch
- Pull requests to `main` or `master`
- Manual trigger via `workflow_dispatch`

## Setup Instructions

### 1. Create Repository
```bash
# Create new repository on GitHub
# Clone it locally
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
```

### 2. Add Workflow File
```bash
# Create workflow directory
mkdir -p .github/workflows

# Copy the workflow YAML to:
# .github/workflows/matrix-build.yml
```

### 3. Add README
```bash
# Update the email address in README.md
# Replace "your.email@example.com" with your actual email
```

### 4. Commit and Push
```bash
git add .
git commit -m "Add matrix build workflow"
git push origin main
```

### 5. Verify Workflow
1. Go to your repository on GitHub
2. Click on the "Actions" tab
3. You should see the workflow running
4. Wait for all jobs to complete
5. Check the artifacts in the workflow run

## Viewing Results

### GitHub Actions Tab
Navigate to: `https://github.com/YOUR_USERNAME/YOUR_REPO/actions`

### Latest Workflow Run
1. Click on the latest workflow run
2. See all 7 matrix jobs completed
3. Scroll to the bottom to see artifacts
4. Download any artifact to inspect contents

### Artifacts Location
Artifacts are available for 30 days and can be downloaded from:
- Individual workflow runs
- Via GitHub API
- Using GitHub CLI: `gh run download RUN_ID`

## Validation Checklist

- [x] **3+ successful matrix jobs**: 7 jobs configured
- [x] **3+ artifacts with prefix**: All 7 artifacts + 1 report
- [x] **Non-empty artifacts**: Each contains build info, metadata, and code
- [x] **Step identifier**: `matrix-5976bde` step included
- [x] **README with email**: Email address at top of README

## Technical Details

### Matrix Strategy Benefits
1. **Parallel Execution**: All jobs run simultaneously
2. **Resource Efficiency**: Reuses workflow definition
3. **Comprehensive Testing**: Multiple environments covered
4. **Easy Scaling**: Add more variants by updating matrix

### Workflow Jobs

#### Job 1: matrix-build
- Runs on all matrix combinations
- Sets up Node.js environment
- Generates build artifacts
- Uploads platform-specific builds

#### Job 2: collect-artifacts
- Depends on matrix-build completion
- Downloads all artifacts
- Creates summary report
- Uploads combined report

## Troubleshooting

### Workflow Not Running
- Ensure the workflow file is in `.github/workflows/`
- Check that you've pushed to `main` or `master` branch
- Verify repository has Actions enabled

### Artifacts Not Appearing
- Check that all jobs completed successfully
- Verify artifact upload step didn't fail
- Ensure artifact retention period hasn't expired

### Build Failures
- Check individual job logs for errors
- Verify Node.js version compatibility
- Ensure all required files are committed

## Repository Structure
```
.
├── .github/
│   └── workflows/
│       └── matrix-build.yml
├── README.md
└── (other project files)
```

## License
MIT License - Feel free to use this workflow in your projects!

## Additional Resources
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Matrix Builds Guide](https://docs.github.com/en/actions/using-jobs/using-a-matrix-for-your-jobs)
- [Artifact Upload/Download](https://github.com/actions/upload-artifact)

---

**Built with ❤️ using GitHub Actions**
