# OpenClaw Update Instructions

Use this workflow every time we want to ship updates to our Railway template.

## 1) Make changes locally

Edit files in this repo:

- `Dockerfile.prebuilt` (default fast path)
- `Dockerfile` (fallback/source-build path)
- `src/*` (wrapper behavior)

## 2) Test locally

```bash
docker build -f Dockerfile.prebuilt -t openclaw-template-fast:local .
```

## 3) Commit + push

```bash
git add .
git commit -m "Describe the update"
git push origin main
```

## 4) Redeploy / reprovision

New Railway deploys will pull from this repo and use:

- Dockerfile path: `Dockerfile.prebuilt`
- Repo: `dangelo352/openclaw-railway-template-fast`
- Branch: `main`

## 5) If Railway deploy fails

Check Railway build logs first. Common causes:

- Dockerfile syntax regressions
- Missing cache mount `id=` values
- Registry/network pull issues

