---
description: >-
  These instructions will help to ensure we don't introduce unwanted changes to
  the lock file.
---

# 🔓 Keeping the lock file in sync

Since we use some private modules alongside the public monorepo, we have some special requirements when dealing with lock file changes. This can be confusing for [some contributors](https://github.com/calcom/cal.com/issues/10436) and there's [some discussion](https://github.com/calcom/cal.com/issues/10217) around it as well.

The rule of thumb is: As long a we don't introduce new packages (either in a package.json or monorepo package) there shouldn't be any lock file changes in a core contributor local environment.&#x20;

### For core-contributors, how to ensure a consistent setup for submodules

*   Make sure you're on main

    ```bash
    git checkout main
    ```
*   Make sure you have private submodules initialized and updated

    ```bash
    ./git-setup.sh website console
    ```
*   Run yarn install to see if there are lock file diffs

    ```bash
    yarn
    ```

### For external contributors

Please refer to the ["Guidelines for committing yarn lock file"](https://github.com/calcom/cal.com/blob/main/CONTRIBUTING.md#guidelines-for-committing-yarn-lockfile) section in our [CONTRIBUTING.md guide](https://github.com/calcom/cal.com/blob/main/CONTRIBUTING.md).
