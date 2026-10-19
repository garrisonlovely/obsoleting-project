# obsoletingproject.com

## How this site deploys (read before saying anything is "live")

- **Production is Cloudflare Pages, not Netlify.** The domain's DNS is on Cloudflare and points at the Pages project `obsoletingproject` (`obsoletingproject.pages.dev`).
- `.github/workflows/deploy-cloudflare-pages.yml` uploads `main` to that project on every push. Its last step fetches obsoletingproject.com and fails unless the live homepage matches `index.html` at that commit. So a green run means the site is live; anything else means it is not.
- It uses the repository secret `CLOUDFLARE_API_TOKEN` (Account → Cloudflare Pages → Edit). The secret already exists; don't ask Garrison for it again unless a run says it's missing or rejected.
- **Netlify** (site `obsoletingproject`) builds deploy previews for pull requests (`deploy-preview-<N>--obsoletingproject.netlify.app`) and serves obsoletingproject.netlify.app. Nothing on Netlify reaches the real domain.
- From April to October 2026, nothing pushed here reached the live site (the Pages project was a one-off manual upload). If you find something like that again on Garrison's other sites, check DNS and the serving host first.

## Working with Garrison

- When a change is done, give him a URL he can open. For production that's https://obsoletingproject.com, after the deploy run is green. For unmerged work, open a PR and give the Netlify deploy-preview link.
- Don't call something live or deployed until you've confirmed it, from the workflow's verify step or an equivalent fetch of the real domain.
- Every quotation and figure on the page is sourced in the Notes list. Keep it that way: verbatim quotes, numbered notes in reading order.
