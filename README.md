# orbh-profiles

Canonical default [Orbh](https://github.com/NUU-Cognition) runtime profiles, synced across machines.

## How it works

Orbh resolves profiles from **two files** in `~/.nuucognition/orbh/`:

| File | Role | Synced? |
|------|------|---------|
| `default.json` | Canonical, team-maintained profiles (this repo) | **Yes** — overwritten by `flint orbh profiles update` |
| `profiles.json` | Your personal profiles / overrides | **No** — never touched by sync |

At load time Orbh merges them: `default.json` is the base, and `profiles.json`
overrides or adds entries per profile key. So your personal profiles always win
and always survive an update.

## Commands

```bash
flint orbh profiles update        # pull the latest default.json from this repo
flint orbh profiles push          # publish your local default.json here (maintainers)
flint orbh profiles push -m "..." # ...with a commit message
```

## Do not hand-edit `default.json` locally

`update` overwrites it. Put anything personal in `profiles.json` instead — that
file is yours and is never synced. `default.json` carries a `"//"` banner key as
a reminder; Orbh ignores that key when loading.
