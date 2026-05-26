# Industry Radar Share

Temporary GitHub Pages package for the 2026-05-25 industry radar report.

- Entry page: `index.html`
- Expiry timestamp: `2026-06-02T10:59:55Z`
- Expiry behavior: `.github/workflows/expire.yml` checks hourly and replaces `index.html` with `expired.html` after the timestamp.

## Publish Steps

1. Create a new GitHub repository named `industry-radar-share`.
2. Push this folder to the repository.
3. In GitHub, open `Settings -> Pages`.
4. Set source to `Deploy from a branch`, branch `main`, folder `/root`.
5. The report URL will be `https://<your-github-username>.github.io/industry-radar-share/`.
