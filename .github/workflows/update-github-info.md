---
name: update-github-info
description: Updates GitHub blog information in the site repository

on:
  schedule:
    - cron: '0 9 * * *'  # Daily at 9 AM UTC
  workflow_dispatch: {}

permissions:
  contents: read
  issues: read
  pull-requests: read

tools:
  web-fetch: null
  edit: null
  github: null

safe-outputs:
  create-pull-request: null

network:
  allowed:
    - github
---

# Update GitHub Info Workflow

## Task

You are an agent that helps keep GitHub blog information up-to-date in the repository. 

### What to do:

1. **Read the current context** by reviewing `notes/mona-notes.md` to understand any specific preferences or guidelines for updating GitHub information.

2. **Fetch the latest GitHub blog content**:
   - Use web-fetch to read https://github.blog/latest/
   - Use web-fetch to read https://github.blog/changelog/

3. **Update the site content**:
   - Based on what you've read from the blog and changelog, update `site/content/github-info.md` with:
     - Key recent announcements from GitHub blog
     - Latest changelog entries
     - Any important updates that would be relevant to site visitors
   - Maintain the existing markdown format and structure

4. **Create a pull request**:
   - Use the `create-pull-request` tool with `safe: true` to propose your changes
   - Title: "chore: Update GitHub blog information"
   - Description: Summarize what new GitHub blog information was added and from which sources
   - Assign the PR for Mona's review
   - Include a link to the sources (github.blog/latest and github.blog/changelog) in the PR description

### Important Guidelines:

- Only update the content if there are meaningful changes to report
- Preserve existing content structure and formatting
- Use clear, concise language appropriate for the site
- When pulling external content, summarize rather than copy entire articles
- Always cite the source (GitHub blog or changelog)

## Execution

Follow the steps above in order. If any step fails, explain what went wrong and what recovery actions you attempted.
