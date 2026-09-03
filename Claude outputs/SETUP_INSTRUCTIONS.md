# How to make this your GitHub profile page

GitHub shows a special README on your profile home page only if it lives in a
repo with the **exact same name as your username**.

## 1. Create the special repo
1. Go to GitHub → New repository.
2. Name it exactly: `itz-Maheshkumar`
3. Make it **Public**.
4. Check "Add a README file", then create it.

## 2. Add the README
Replace the auto-created `README.md` in that repo with the `README.md` file
provided — either edit it directly on GitHub (pencil icon) or push it locally:

```bash
git clone https://github.com/itz-Maheshkumar/itz-Maheshkumar.git
cd itz-Maheshkumar
# copy the new README.md into this folder, replacing the old one
git add README.md
git commit -m "Add custom profile README"
git push
```

## 3. (Optional but recommended) Enable the contribution snake animation
This makes a snake "eat" your contribution graph — the wow-factor section in
the README references it.

1. In the same `itz-Maheshkumar` repo, create the folder path
   `.github/workflows/snake.yml` and paste in the provided `snake.yml`.
2. Go to repo **Settings → Actions → General → Workflow permissions** and
   select **"Read and write permissions"**, then Save.
3. Go to the **Actions** tab and manually run "Generate Snake Animation" once
   (or just wait — it also runs on every push and every 6 hours).
4. It creates an `output` branch with the generated SVGs — the README already
   points at that branch, so once it runs, the animation appears automatically.

## 4. Replace the broken stats cards with self-hosted metrics
The old stats/activity-graph images used `github-readme-stats.vercel.app` and
`github-readme-activity-graph.vercel.app` — free public demo servers shared by
millions of GitHub profiles, which is why they kept showing as broken images
(rate limits, not a bug in your README). The updated README instead points to
a stats image generated **inside your own repo** by the open-source
[`lowlighter/metrics`](https://github.com/lowlighter/metrics) GitHub Action —
no external live server involved, so it can't randomly break.

1. **Create a Personal Access Token (PAT):**
   GitHub → your profile photo → Settings → Developer settings → Personal
   access tokens → Tokens (classic) → Generate new token. No scopes are
   required for public data (leave them unchecked, or tick `public_repo` if
   you want it to be safe). Copy the token — you won't see it again.
2. **Save it as a repo secret:**
   In the `itz-Maheshkumar` repo → Settings → Secrets and variables → Actions
   → New repository secret → name it `METRICS_TOKEN`, paste the token, Save.
3. **Add the workflow:**
   Create `.github/workflows/metrics.yml` in the repo and paste in the
   provided `metrics.yml` file's content.
4. Push these changes, then go to the **Actions** tab → run "GitHub Metrics"
   manually once (▶ button). It commits `github-metrics.svg` to the `output`
   branch — the same unprotected branch the snake animation already uses, so
   it won't hit the branch ruleset either.
5. Once that run succeeds, the stats image will appear on your profile
   automatically (it also refreshes daily on its own).

If any option in the workflow errors out (the plugin list changes over
versions), open [lowlighter/metrics](https://github.com/lowlighter/metrics)'s
README, use its interactive setup/config builder to pick the exact
plugins you want, and send me the generated YAML — I'll wire it in.

## 5. Fix any repo names/links that don't match
The README links to these repos — rename your actual repos to match (or edit
the links in the README) so the project cards work:
- `Collaborative_Database_Notebook`
- `Semantic_cache_Application`
- `Warehouse_Stock_Management`
- `The_caseworkers_morning`

## 6. Nice-to-haves you can add later
- Pin these 4 repos on your profile (Customize your pins → pick the 4).
- Add a short repo description + topics to each pinned repo — it shows under
  the pin card.
- If you want a live "now doing X" line, GitHub Actions can auto-update the
  README from a script — ask if you want that wired up.
