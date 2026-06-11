# netsectom.com — Blue Team Notes

Static blog. No build step, no framework, no dependencies. Edit HTML, push, done.

## Deploy to GitHub Pages (free) — ~10 minutes

1. **Create the repo.** On GitHub (logged in as `netsectom`), create a new
   public repo named exactly: `netsectom.github.io`

2. **Push these files.**
   ```bash
   cd netsectom
   git init
   git add .
   git commit -m "Plant the tree"
   git branch -M main
   git remote add origin https://github.com/netsectom/netsectom.github.io.git
   git push -u origin main
   ```
   Site is now live at https://netsectom.github.io within a minute or two.

3. **Point your domain.** At your domain registrar, add these DNS records
   for netsectom.com:

   | Type  | Host | Value                |
   |-------|------|----------------------|
   | A     | @    | 185.199.108.153      |
   | A     | @    | 185.199.109.153      |
   | A     | @    | 185.199.110.153      |
   | A     | @    | 185.199.111.153      |
   | CNAME | www  | netsectom.github.io  |

4. **Tell GitHub about the domain.** Repo → Settings → Pages →
   Custom domain → enter `netsectom.com` → Save. Check
   "Enforce HTTPS" once the cert provisions (can take up to an hour).
   The `CNAME` file in this repo keeps the setting from resetting on push.

DNS can take a few hours to propagate. The github.io URL works immediately.

## Writing a new post

1. Copy `posts/detecting-mfa-fatigue-sentinel.html` to a new file:
   `posts/your-post-slug.html` (lowercase, hyphens, descriptive).
2. Update the `<title>`, meta description, date, severity badge, and content.
3. Add a row to the result table in `index.html` — there's a commented
   template block showing exactly what to copy.
4. Bump the "RESULTS — N records" count. (Yes, by hand. It's part of the bit.)
5. Commit and push. Live in ~60 seconds.

## Category badges

- `sev-detection` — detection engineering, KQL, Sentinel rules
- `sev-identity`  — Entra ID, Conditional Access, AD
- `sev-lab`       — homelab builds and walkthroughs
- `sev-ctf`       — CTF writeups

## The rules (from yourself, to yourself)

- Only publish things you actually built and tested. Say where you tested it.
- The bar for every post: would a working SOC analyst find this useful?
- One real post a month beats four shallow ones.
- This supports the job search. It does not replace applying.
