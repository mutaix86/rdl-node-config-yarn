# rdl-node-config-yarn

Test fixture for the `remove_duplicate_lockfiles` maintenance task.

## Scenario

Node conflict at repo root — `package.json` declares **no** `packageManager` field, but `.yarnrc.yml` is present.

Lockfiles:
- `package-lock.json` (npm)
- `yarn.lock` (yarn)

## Expected MT behaviour

- **Auto-detects** yarn via the `.yarnrc.yml` config file — no user question.
- **Deletes** `package-lock.json`, keeps `yarn.lock`.
- **Appends** `package-lock.json` to `.gitignore` under the Autar section header.
