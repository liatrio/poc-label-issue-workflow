# poc-label-issue-workflow

## Introduction

Automate your issue labeling process with our reusable GitHub Actions workflow. Designed for ease of integration, this workflow enables you to quickly add labels to issues as they are opened or reopened, ensuring your project's issues are always categorized correctly.

## How to Use

Integrating this workflow into your project is straightforward.

To start using the workflow in your project, you'll need to create a new file that references the workflow. Here's how you can do it:

1. Within your GitHub repository, navigate to the `.github/workflows` directory. Create one if it doesn't exist.
2. Create a new YAML file for your workflow. This file can be named anything, but it could be something like `auto-label-issues.yml`.
3. Copy and paste the following configuration into your new workflow file:

```yaml
name: Label Workflow

on:
  issues:
    types:
      - opened
      - reopened

jobs:
  call-label-workflow:
    uses: liatrio/poc-label-issue-workflow/.github/workflows/label-issue-workflow.yml@main
    with:
      labels: 'triage'
      issue_number: ${{ github.event.issue.number }}
      repo: ${{ github.repository }}
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

Replace `triage` with the labels you wish. Labels should be a single string with labels separated by commas (e.g. 'new,triage')
