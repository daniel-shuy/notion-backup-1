# `notion-backup`

> Export [Notion](https://www.notion.so/) pages and subpages to a GitHub repo on a schedule (eg. to be used as a scheduled backup)

## Setup

1. Click on the green "Use this template" button at the top to make your own copy of this repository - make sure to choose "Private" visibility, unless you want to make your Notion content visible to the public
2. Give Action workflows read and write permissions to the repository under Settings -> Actions -> General -> Workflow permissions
3. Create a new repo secret under Settings -> Secrets called `NOTION_TOKEN` with the instructions in [this article](https://archive.ph/b5mgg)
4. Edit `index.ts` to add the Notion pages you want to export to the `blocks` array at the top of the file
5. Optional: Edit `index.ts` to specify a different export format, time zone or locale
6. Optional: Edit `.github/workflows/export-notion-blocks-and-commit.yml` to specify a different schedule (default is once per day)
7. After the `Export Notion Blocks and Commit to Git` workflow has run, your backup will have been committed to your GitHub repo in the `exports` folder! 🙌

## How

The GitHub Actions workflow is scheduled to run once a day to:

1. export each specified Notion block
2. wait until each export is done
3. download, unzip and commit the content from each export to the repository

## Credit

This script is heavily based on [`notion-guardian`](https://github.com/richartkeil/notion-guardian), thanks to [@richartkeil](https://github.com/richartkeil)!
