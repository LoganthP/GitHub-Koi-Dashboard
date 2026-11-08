# Setup and deployment

## 1. Create repository

Create a **public** GitHub repository (suggestion: `github-koi-dashboard`) and upload this starter kit to its `main` branch. A separate project repository is recommended; you can keep your existing GitHub profile repository untouched.

## 2. Personalize

Edit `config.js`:

```js
window.KOI_CONFIG = {
  username: 'YOUR_GITHUB_USERNAME',
  displayName: 'Your Name',
  linkedin: 'https://www.linkedin.com/in/YOUR_HANDLE/' // or ''
};
```

The tech-stack badges are intentionally curated HTML in `index.html`; edit their labels for your own skills. Public activity depends on the chosen username, but the workflow generates the fish for the **repository owner**. Use the same username for both unless customizing the action's `login` input.

## 3. Generate koi

Open **Actions → Generate koi → Run workflow**. The action writes `koi/koi.gif`, then commits it. If pushing fails, check repository Actions permissions and any branch protection rules.

The `schedule` requests a daily run at **00:20 UTC**; GitHub may delay or skip it. The workflow runs by default from the default branch. Scheduled workflows can be disabled after long repository inactivity.

## 4. Deploy

Open **Settings → Pages**, then select **Source: GitHub Actions**. The included `Deploy GitHub Pages` workflow publishes the repository root. The URL for project `github-koi-dashboard` will be:

`https://YOUR_GITHUB_USERNAME.github.io/github-koi-dashboard/`

Do **not** select 'Deploy from a branch' when using the included Pages workflow; choose one deployment method.

## 5. Embed in a profile README

Use this in your profile README (replace both placeholders):

```html
<p align="center">
  <a href="https://YOUR_GITHUB_USERNAME.github.io/github-koi-dashboard/">
    <img src="https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/github-koi-dashboard/main/koi/koi.gif" width="256" alt="Animated GitHub Koi" />
  </a>
</p>
<p align="center"><a href="https://YOUR_GITHUB_USERNAME.github.io/github-koi-dashboard/">Explore the interactive Koi dashboard</a></p>
```

GitHub READMEs cannot run JavaScript. The drag controls and charts work on GitHub Pages, not inside the profile README.

## 6. Troubleshooting

- **Fish missing:** workflow has not generated `koi/koi.gif`, or the branch did not receive the generated commit.
- **Pages 404:** Pages source must be GitHub Actions and the deployment workflow must succeed. Verify repository name and case-sensitive URL path.
- **Events empty:** public Events API is limited to recent public history and may be rate-limited; use the refresh button or inspect browser Developer Tools → Network. Missing events are not equivalent to zero GitHub contributions.
- **Calendar unavailable:** third-party contribution service may be down or cached; the aquarium still works.
- **Different fish than profile:** action defaults to the repository owner; match the `login` parameter to `config.js` username when needed.
- **Forks:** GitHub Actions may be disabled initially on a fork; manually enable in Actions settings.
