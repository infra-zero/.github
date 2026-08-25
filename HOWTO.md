# Org profile READMEs

This repo **is** `github.com/infra-zero/.github`. Its `profile/README.md` renders
at `github.com/infra-zero` within a minute or so of a push to `main`.

```
profile/README.md   ->   github.com/infra-zero
```

Both the repo name and the file path are load-bearing. There is no config, no
setting, no alternative location — rename either and the profile page silently
goes blank with no warning anywhere in the UI.

## Setting this up for another org

If the org already has a `.github` repo (org-wide issue templates and shared
workflows live there too), just drop `profile/README.md` into it — no new repo
needed. Otherwise:

```sh
ORG=some-org
gh repo create "$ORG/.github" --public --description "Org profile, issue templates, shared workflows"
git clone "https://github.com/$ORG/.github" /tmp/$ORG-dotgithub
mkdir -p /tmp/$ORG-dotgithub/profile
cp profile/README.md /tmp/$ORG-dotgithub/profile/
git -C /tmp/$ORG-dotgithub add profile && \
  git -C /tmp/$ORG-dotgithub commit -m "docs: add org profile README" && \
  git -C /tmp/$ORG-dotgithub push
```

**If a repo already holds the content under the wrong name** — as this one did,
as `infra-zero/infra-zero` — rename it instead of creating a second repo. Keeps
history and issues, and GitHub leaves a redirect from the old name:

```sh
gh api -X PATCH repos/$ORG/$OLD_NAME -f name=.github
git remote set-url origin git@github.com:$ORG/.github.git
```

## Notes

- The `.github` repo must be **public** or the profile won't render, even for an
  org whose repos are private.
- A members-only variant goes in a separate `.github-private` repo, same
  `profile/README.md` path. That repo can be private.
- **No snake.** The contribution-graph snake in `rtorcato/rtorcato` is generated
  from a *user's* contribution calendar; orgs don't have one. Shields badges,
  stars, and static content all work.
- `img.shields.io/github/stars/<org>` does aggregate stars across the org's
  public repos — verified. Not currently used on the profile: at this star count
  the badge undersells rather than sells.
- Badge colors follow the same convention as the personal profile —
  `style=for-the-badge`, `labelColor=1a1a1a`, accent from
  `shared-docs/src/family.ts` where the project has one (infra-x `2dd4bf`,
  db-x `10b981`).
- **Half the profile page isn't this file.** GitHub renders the org description
  above the README, and it starts out empty — set it with
  `gh api -X PATCH orgs/<org> -f description='...'`. Repo topics and homepage
  fields drive discovery from the org's repo list.

## TODOs left in the files

- `infrazero-platform` is private, so it's deliberately not linked from the
  projects table. Add a card when it opens.
