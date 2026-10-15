# tahmids-artifacts

Static pages served at https://artifacts.tahmid.dev via a Cloudflare Worker with static assets.

## Layout

- `public/index.html` — index page listing every artifact
- `public/<slug>/index.html` — one folder per artifact

## Adding an artifact

Use the `publish-artifact` Claude skill, or by hand:

```
python3 ~/.claude/skills/publish-artifact/scripts/add_artifact.py page.html \
  --slug my-page --title "My Page" --summary "One sentence for the index card."
```

The script copies the page to `public/<slug>/index.html`, registers it in `artifacts.json`,
regenerates `public/index.html` (never edit it by hand), commits and pushes. The GitHub Action
deploys with wrangler on every push to `main`.

## Manual deploy

```
npm install
npx wrangler deploy
```

The GitHub Action needs the repository secrets `CLOUDFLARE_API_TOKEN` (Workers Scripts edit, Zone DNS edit for tahmid.dev) and `CLOUDFLARE_ACCOUNT_ID`.
