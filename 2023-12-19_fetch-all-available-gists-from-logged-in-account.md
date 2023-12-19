## Fetch all available gists from logged in account

You can use the GitHub API in order to download a list of all public and private gists from a logged in account (i.e. Bearer token):

```bash
curl -L \                                                                                                        ─╯
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer $(secret-tool lookup keyId GitHubPersonalAccessToken)" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  https://api.github.com/gists
```

