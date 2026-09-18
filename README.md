# Bolster Juniors — Hosted Pages

Static, self-contained web pages for the **Bolster Juniors Desk** school-management app, served via **GitHub Pages** from this repository.

These pages are published at:
- **Privacy Policy** — `https://the-shed-of-jaga.github.io/bolsterjuniors-pages/privacy-policy/`
- **Account Deletion** — `https://the-shed-of-jaga.github.io/bolsterjuniors-pages/deletion-page/`

Both URLs are submitted to the **Google Play Console** (Data safety → Privacy policy / App content → Account deletion) and are required to keep the app listed on the Play Store.

## Repo Contents

| Path | Purpose |
|------|---------|
| `privacy-policy/` | Privacy Policy page — a plain-HTML copy of the in-app policy screen (all 16 sections: Introduction, Data Collected, Google Sign-In, Data Sharing, Security, Retention, Your Rights, Account Deletion, etc.). |
| `deletion-page/` | Account-deletion page — a form that submits a deletion request directly to the Supabase `request_account_deletion` RPC for the app's `auth.users` account. |

Each folder also ships the logo assets it renders (`bolster_juniors_app_logo.png` + dark-mode `bolster_juniors_dark_color_mode_logo.svg`).

## How Pages serves them

No build step, no framework — each `index.html` is a fully self-contained static page (inline CSS/JS).

1. A change is pushed to the `master` branch.
2. GitHub Pages (repo → **Settings → Pages → Source: Deploy from a branch → `master`/`/ (root)**) publishes the folder as a site rooted at `/(root)`.
3. Because the site root is `/`, each page lives at the sub-path shown above.

## Keeping the policy in sync

> ⚠️ **The privacy policy exists in three independent copies and all must stay in sync.**

| Copy | Sync trigger |
|------|--------------|
| `privacy-policy/index.html` here | Every edit must be **pushed** to this repo to reach the live URL |
| In-app screen | `lib/screens/privacy_policy_screen.dart` in the main app repo — ships with each app release |
| `deletion-page/index.html` here | Updated only when the deletion copy changes |

Any change to the policy text must be made in **both** the HTML here *and* the Dart screen, then pushed/app-released respectively.

## Deploying an update

```bash
git add -A
git commit -m "Update privacy policy"
git push origin master
```

That's it — GitHub Pages re-deploys automatically (usually within ~1 minute).

## Related repositories

- **App source** — [`jagadishcts/bolsterjuniors`](https://github.com/jagadishcts/bolsterjuniors): the Flutter + Supabase school-management app (Android/Web).
- Supabase project: `https://kvnxejgssxtvadkuqyyk.supabase.co`

## License

© Bolster Juniors. Static pages hosted for public access; no warranty implied.