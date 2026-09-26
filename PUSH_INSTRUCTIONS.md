# Push instructions — boku-contributions

No `gh` CLI found on this machine, so push manually (2 min).

## Option A: GitHub web (easiest, no git needed)

1. Go to https://github.com/new
   - Owner: `Optional-BhanuPrakash`
   - Name: `boku-contributions`
   - Public, no README/license/gitignore.
2. Click **uploading an existing file** → drag ALL files from `boku-contributions/` (including `.github/`).
   - If `.github` is hidden in picker, zip the folder and upload via `Add file → Upload files` still works — or use Option B.
3. Commit to `main`.
4. Settings → Actions → General → Workflow permissions → **Read and write permissions** → Save.
5. Actions → run each workflow once via **Run workflow**:
   - Update Maeul in the Sky
   - generate arcade contribution graphs
   - Build CRT contribution SVGs
   - Generate snake animation
   - Metrics 3D city + stats
6. Wait 2–5 min, check `output` branch appears (arcade+snake), `assets/` + `*.svg` on main.

## Option B: git (if installed)

```powershell
cd C:\Users\bhanu\Downloads\boku\boku-contributions
git init -b main
git add .
git commit -m "feat: all 6 contribution visuals"
git remote add origin https://github.com/Optional-BhanuPrakash/boku-contributions.git
git push -u origin main
```

Then same step 4–5 above.

## After first run

- Copy embed snippets from `README.md` into https://github.com/Optional-BhanuPrakash/Optional-BhanuPrakash `README.md`.
- For profile repo, change `raw.githubusercontent.com/.../boku-contributions/...` URLs stay as-is (cross-repo embeds work).
- Snake + arcade share `output` branch: if one overwrites the other, stagger crons (edit `arcade.yml` to `30 1 * * *`).
- Streak card: if `herokuapp` URL is down, use `streak-stats.demolab.com?user=Optional-BhanuPrakash&...&animated=true` (maintained fork).
- Activity graph must use `github-readme-activity-graph.vercel.app` (Heroku/Cyclic dead).
- Metrics WakaTime/LeetCode need `METRICS_TOKEN` secret — add later.
