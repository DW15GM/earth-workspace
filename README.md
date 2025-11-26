# Earth Workspace

This is the **Virtual Monorepo** for the Earth Project. It unifies the tooling for our multi-repo ecosystem without merging the repositories themselves.

## Setup

1.  **Clone this workspace:**
    ```bash
    git clone git@github.com:DW15GM/earth-workspace.git
    cd earth-workspace
    ```

2.  **Install tools:**
    ```bash
    npm install
    ```

3.  **Clone all sub-repos:**
    ```bash
    npm run setup
    # This runs 'meta git clone' to fetch earth-core, earth-ads, etc.
    ```

## Usage

### 1. Sync All Repos
Update all sub-repositories to their latest `main` branch:
```bash
npm run sync
```

### 2. Check Status (Unified Control Plane)
Get the aggregated status of PRs, CI, and Deployments:
```bash
npm run status -- --pr=123
```

## Directory Structure
*   `.meta`: Configuration mapping sub-repos to git URLs.
*   `tools/cli`: Source code for the `earth` CLI.
*   `earth-core/`, `earth-ads/`: Cloned sub-repositories (ignored by git).

## Deployment
**None.** This repository is a **Local Development Tool**. It should **NOT** be deployed to Render, Vercel, or any production server. It lives only on:
1.  Developer Laptops
2.  Agent Workspaces (CI/CD Runners)

