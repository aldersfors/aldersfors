# aldersfors

Shared [Renovate](https://docs.renovatebot.com/) preset for the `aldersfors` org.

## Usage

```json5
{
  $schema: "https://docs.renovatebot.com/renovate-schema.json",
  extends: ["github>aldersfors/aldersfors:default.json5"],
}
```

The `:default.json5` suffix is required. The bare `github>aldersfors/aldersfors`
shorthand only resolves `default.json`. The preset is JSON5 so every setting can carry
a comment explaining why it is there; read `default.json5` for the reasons.

## What it sets

- `config:recommended`, semantic commits, `dependencies` label, `Europe/Stockholm`.
- 5-day minimum release age; dependencies with no release in a year are flagged abandoned.
- Minor, patch and digest updates automerge, weekdays 09:00-20:59. Renovate merges
  itself (`platformAutomerge: false`); majors wait for review.
- Go: indirect modules are updated and `go mod tidy` runs after each update.
- Test directories are scanned for dependencies.
- OSV and GitHub vulnerability alerts, labelled `security`.

Repo-specific managers and rules stay in each repo's own Renovate config.

## Development

`mise run ci` runs `renovate-config-validator --strict` on both config files, the same
check CI runs. A change here applies to every repo on its next Renovate run.
