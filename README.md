# tahmids-artifacts

Static pages served at https://artifacts.tahmid.dev via a Cloudflare Worker with static assets.

## Layout

- `public/index.html` — index page listing every artifact
- `public/<slug>/index.html` — one folder per artifact

## Adding an artifact

1. Drop the standalone HTML at `public/<slug>/index.html`
2. Add a card for it in `public/index.html`
3. Push to `main`; the GitHub Action deploys with wrangler

## Manual deploy

```
npm install
npx wrangler deploy
```

The GitHub Action needs the repository secrets `CLOUDFLARE_API_TOKEN` (Workers Scripts edit, Zone DNS edit for tahmid.dev) and `CLOUDFLARE_ACCOUNT_ID`.
