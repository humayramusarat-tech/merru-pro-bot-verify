# VIP affiliate helper — GitHub and Railway

This is the small helper service only; it is not the whole VIP bot project.

## 1. Put the files in GitHub

Extract this ZIP on your computer. Create a new, private GitHub repository, then upload these three files to the repository's top level:

- `helper.py`
- `requirements.txt`
- `railway.json`

Do not upload the full Lovable project. `make_session.py` is only for creating a Telegram login session on your own computer; it is not needed by Railway. Never upload session text, API hashes, passwords, or other credentials to GitHub.

## 2. Connect the repository to Railway

In Railway, choose **New Project → Deploy from GitHub Repo**, select this repository, and deploy it. Railway reads `railway.json` and installs the packages from `requirements.txt`.

## 3. Add Railway variables

In the Railway service's **Variables** settings, add:

- `TG_API_ID` — Telegram API ID
- `TG_API_HASH` — Telegram API hash
- `TG_SESSION` — session text generated with `make_session.py`
- `AFFILIATE_BOT` — affiliate bot username, such as `@example_bot`
- `APP_URL` — `https://trader-vip-gatekeeper.lovable.app`
- `VERIFIER_SECRET` — the same verifier secret configured for the VIP app

Optional settings: `POLL_SECONDS` (default `5`) and `REPLY_TIMEOUT` (default `40`).

Keep all values in Railway Variables, never in GitHub. `TG_SESSION` grants access to your Telegram account; treat it like a password and do not share it.

## Create `TG_SESSION`

On your own computer, run `make_session.py` with Python and Telethon installed. It asks for your Telegram API ID, API hash, phone number, and Telegram login code, then prints the session text. Paste that text directly into Railway's `TG_SESSION` variable; do not commit it to GitHub.
