# What this repo actually is

This repo is not an app. It's the special one: GitHub reads a repo named
exactly `landonkea` (matching the account name) and, if it has a README.md,
shows that file on the profile page at github.com/landonkea. That's the
entire mechanism. One markdown file, one convention GitHub already supports.

Worth saying plainly because it's easy to over-think: there's no server, no
build step, no database, nothing "running." The only thing GitHub does with
this repo is render README.md as HTML on the profile page.

## If this repo got deleted, here's the whole rebuild

1. Create a new repo under the `landonkea` account named `landonkea`.
   The name has to match the username exactly. That's the only part GitHub
   cares about.
2. Add a README.md.
3. Push it.

That's it. Nothing to configure, no secrets to restore, no data to migrate.
The GitHub stats widget in the README (the `github-readme-stats.vercel.app`
image) is a hosted third-party service, not something this repo runs. There's
nothing to redeploy there either, it just needs the username in the URL to
still be `landonkea`.

## History worth keeping in mind

Three commits, all real content changes, no throwaway ones:

- `34235a6` — initial README, July 29, 2026. A short first pass.
- `b1b6475` — Aug 8, 2026. Expanded a short bio into the full version:
  hobbies, philosophy, the "Highly Disputed Rumors" section, all added here.
  This is where the README became what it is now, tone-wise.
- `1e96a57` — Aug 9, 2026. A wording pass over that same content, 12 lines
  changed each direction, no structural changes.

Nothing here needs a changelog or version tags. It's small enough that
`git log` already is the changelog.

## Dev / staging / prod

Doesn't apply, and forcing it here would just be theater. There's no
runtime to stage anything in. The "deploy" is GitHub reading a file out of
`main`, full stop. Any dev/staging/prod split would mean maintaining fake
environments for a static text file, which adds process without protecting
against anything real.

What a profile README repo actually benefits from is smaller: making sure
the markdown itself isn't broken before it goes live. That's what the CI
workflow in `.github/workflows/ci.yml` does. It runs markdownlint against
README.md on every push and pull request, catching things like a missing
close-bracket on a link or a heading with a stray character before either
shows up broken on the actual profile page. `.markdownlint.json` in this
repo turns off a few rules (line-length, first-line-must-be-h1,
no-trailing-punctuation-in-headings) that would otherwise flag the README's
normal prose style as errors. Those aren't mistakes, they're just how this
README is written.
