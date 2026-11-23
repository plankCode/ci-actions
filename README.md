# Shared CI actions

## `publish-openartifact`

Zips build outputs and uploads them to the `builds` raw repository on
`https://artifactory.plankbyte.com`.

Workflows must pass `secrets.OPENARTIFACT_TOKEN` as the `token` input. The
token is a deploy token, not the admin password, and is stored as a repository
secret in each calling repo.

Artifacts are stored at:

```
builds/ci/<repo>/<ref>/<run-id>/<short-sha>/<name>.zip
```

Usage:

```yaml
- uses: plankCode/ci-actions/.github/actions/publish-openartifact@main
  with:
    name: my-build
    token: ${{ secrets.OPENARTIFACT_TOKEN }}
    paths: |
      dist/
      !dist/unneeded/
```
