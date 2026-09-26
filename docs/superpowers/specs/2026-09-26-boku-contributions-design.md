# Design: boku-contributions (2026-09-26)

## Intent
Showcase all 6 contribution visual types from screenshots for `Optional-BhanuPrakash` in one public repo with daily Actions.

## Decision
Approach A: Full Actions monorepo `boku-contributions`. Rejected B (URL-only, fragile) and C (split repos, extra setup).

## Mapping (image → implementation)
1. Maeul village → `t1seo/maeul-in-the-sky@v2.1.0`, preset balanced, snapshot on, `maeul.yml`.
2. Arcade 6 games → `abozanona/pacman-contribution-graph@main`, games `pacman,breakout,galaga,puzzle-bobble,bomberman,minesweeper`, push to `output`, `arcade.yml`.
3. CRT dashboard → `stefashkaa/github-profile-crt@v1`, themes `crt,amber,ice,winamp,neon`, `assets/`, `crt.yml`.
4. 3D cities → `lowlighter/metrics@latest` isocalendar (+ CommitPulse badge URL, radiumcoders app as manual link), `metrics.yml`.
5. Snake → `Platane/snk@v3` svg+gif to `dist/` → `output`, `snake.yml`.
6. Stat cards → Vercel activity-graph + streak-stats (ANIMATED fork) + metrics base svg, README-only.

## Architecture
- `main`: code + README + `assets/`, `metrics.*.svg`, `maeul-*.svg`.
- `output`: arcade + snake SVGs via `crazy-max/ghaction-github-pages@v3.1.0` (`build_dir: dist`).
- All workflows: `schedule cron` + `workflow_dispatch`, `contents: write`, GITHUB_TOKEN only.

## Risks
- Snake + arcade share `output`/`dist` → stagger crons if clobbered.
- Heroku streak/activity URLs dead → use Vercel/demolab hosts.
- `gh` CLI absent → manual web push (see PUSH_INSTRUCTIONS.md).

## Self-review
No TBDs. User/repo names pinned. Versions pinned (maeul v2.1.0, snk v3, crt v1, pacman main). Dark/light `<picture>` embeds verified against upstream READMEs 2026-09-26.
