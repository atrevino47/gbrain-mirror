# gbrain-mirror

Nightly disaster-recovery mirror of [garrytan/gbrain](https://github.com/garrytan/gbrain).

## What this is

This repo is a pure mirror of `garrytan/gbrain` kept up to date by a nightly GitHub Actions workflow. Its only purpose is insurance: if upstream ever becomes unavailable (rare — GitHub outage, policy change, repo deletion), Forge still has a recoverable copy.

## How it works

- **Schedule:** daily at 05:00 UTC (00:00 America/Monterrey CDT)
- **Mirror target:** `refs/heads/upstream/*` and `refs/tags/*`
- **Workflow:** `.github/workflows/nightly-mirror.yml`
- **Trigger manually:** Actions → Nightly Mirror → Run workflow

The `main` branch of this repo holds only the workflow file and this README — it is never touched by the mirror job.

## How to recover from it

If `garrytan/gbrain` is unavailable:

```bash
git clone https://github.com/atrevino47/gbrain-mirror.git
cd gbrain-mirror
git checkout upstream/master    # or whatever the upstream default branch is
bun install
bun link
```

That gives you a working gbrain CLI from the last successful nightly mirror snapshot.

## Relationship to the fork

This is **separate** from [atrevino47/gbrain](https://github.com/atrevino47/gbrain), which is the working fork where Forge's Claude Code host adapter is developed. The fork evolves; the mirror is read-only insurance.

## License

Mirrors upstream MIT license from garrytan/gbrain.
