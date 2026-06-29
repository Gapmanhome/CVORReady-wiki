# Push this repo

Remote is already configured (`origin` -> https://github.com/Gapmanhome/CVORReady-wiki.git)
and branch is `main`, so from the unzipped folder you only need:

```
cd cvorready-wiki
git push -u origin main
```

When prompted for a password, paste a **Personal Access Token** (not your GitHub login
password). Make one at: Settings -> Developer settings -> Personal access tokens
(fine-grained, scoped to CVORReady-wiki, or classic with the `repo` scope).

Note: the GitHub repo is named `CVORReady-wiki`; the local folder is `cvorready-wiki`.
That mismatch is fine — the remote URL is what matters, and it's set correctly.
