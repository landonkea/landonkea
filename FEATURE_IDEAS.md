# Feature Ideas

Concrete ideas for the profile README, based on what's actually in
`README.md` today: a bio, a hobbies list, a philosophy section, a joke
section ("Highly Disputed Rumors"), a "Currently Building" list of five
projects with no links, one GitHub stats image, and a closing line. Nothing
below repeats what's already there — these are additions or upgrades to
specific sections.

## Linking the work that already exists

1. **Link the "Currently Building" projects.** `README.md` lines 103-107
   name five projects (Make It So Number One, Apple Products Scraper,
   ThinkLessScheduleMore, Soliloquy, StorageFinder) but none of them link
   anywhere. A visitor who wants to see the actual code has to go search
   GitHub for it. Turning each bullet into `[Make It So Number One]
   (https://github.com/landonkea/landonkea-makeItSoNumberOne)` costs nothing
   and is the single most useful change on this list.

2. **A "More of the Fleet" section.** There are close to 30 `landonkea-*`
   repos on this account and the README only names 5. A short section
   grouping a handful more by kind - say, `landonkea-cli-tools`,
   `landonkea-dad-jokes-api`, `landonkea-task-manager-web` under "tools and
   apps," and `landonkea-python-learning-exercises` /
   `landonkea-ruby-learning-exercises` under "learning in public" - gives
   visitors a map instead of a dead end after the five pinned projects.

3. **Curate GitHub's actual pinned-repo row.** Separate from README content:
   GitHub lets an account pin up to 6 repos above the README on the profile
   page. Right now whatever's pinned (or not) is disconnected from the
   "Currently Building" list. Picking pins that match that list would make
   the two sections reinforce each other instead of showing different
   projects.

## Visual / stats widgets

4. **Swap the stats image for a themed picture element.** Line 111 hardcodes
   `theme=dark` on the github-readme-stats image, so it looks wrong for
   anyone viewing GitHub in light mode. A `<picture>` element with a
   `prefers-color-scheme` media query, one light-themed image and one
   dark-themed image, fixes that without extra tooling.

5. **Add a top-languages card.** github-readme-stats also has a
   `/api/top-langs` endpoint. Next to the existing stats card, it would show
   an actual breakdown of what's been used across the fleet (Ruby, Python,
   JS/TS, Go, C#, Java, Swift for `landonkea-ytmusic-ios`) instead of making
   a visitor guess from project names.

6. **A streak-stats widget.** `github-readme-streak-stats` shows current
   and longest contribution streaks. Given the "Currently Building" section
   already signals active work, a streak counter backs that up with a
   number instead of just a claim.

7. **A GitHub trophies row.** `github-profile-trophy` renders badges for
   things like commit count, stars, and followers. It's a lighter, more
   playful widget than a stats table, and it fits the tone of the "Highly
   Disputed Rumors" section better than another dense chart would.

## Content sections

8. **Tech-stack badge row.** A row of shields.io badges (Ruby, Python,
   JavaScript/TypeScript, Go, C#/.NET, Java, Docker) placed near the top,
   under the intro. Right now the only way to know what languages this
   account works in is to click through to individual repos.

9. **A "Currently Learning" section.** The hobbies list already says
   "Teaching myself completely unnecessary skills simply because they
   looked fun" (line 22), but there's no section that names what those
   skills currently are. A short, three-or-four-line list next to "Currently
   Building" would turn that joke into something concrete and would double
   as a natural place to update every few months.

10. **A short "How this README works" line.** Something like `*curious how
    this page works? [see the notes](docs/DESIGN.md)*` near the bottom.
    Small, but it fits someone who describes themselves as constantly
    asking "why does this happen" (line 9), and it's a natural link to the
    resurrection doc added alongside this file.

11. **A table of contents at the top.** The README is 117 lines with eight
    distinct sections. A short jump-link list right after the intro (`Who is
    Landon? · Hobbies · Philosophy · Disputed Rumors · Currently Building`)
    would help anyone skimming on mobile, where the whole page is several
    screens of scrolling.

12. **Collapse the "Highly Disputed Rumors" section.** It's 20 bullet
    points (lines 56-77), the longest section in the file. Wrapping it in a
    `<details><summary>Highly Disputed Rumors</summary>...</details>` block
    would let it stay exactly as long and as weird as it is, while keeping
    the page shorter for anyone who wants to jump straight to "Currently
    Building" or the stats.

13. **A photo or two.** The hobbies list mentions "Photographing storms,
    unusual architecture, weird signs, old machinery" (line 25) but the
    README is text-only. Even one or two real images, dropped into an
    `<img>` tag under that bullet, would back up the claim with something a
    visitor can actually see.

## Automation

14. **Auto-update "Currently Building" from real repo activity.** A
    scheduled GitHub Action that hits the GitHub API for recently-pushed
    `landonkea-*` repos and rewrites a marked section of the README (the
    common `<!-- ACTIVITY:START -->` / `<!-- ACTIVITY:END -->` comment-block
    pattern) would keep that list honest without manual edits every time a
    project gets picked up or set down.

15. **A visitor counter.** A simple badge like
    `https://komarev.com/ghpvc/?username=landonkea` gives a rough sense of
    profile traffic. Low effort, and it's a common enough profile-README
    addition that it wouldn't look out of place next to the stats card.

16. **Social/contact links row.** The only link in the whole file right now
    is the GitHub link on the last line (117). A short row of icons or text
    links (LinkedIn, a personal site, email) would give a future
    collaborator - the audience the closing section (lines 92-94) is
    explicitly written for - somewhere to actually go.

## Housekeeping

17. **A markdownlint badge.** Once the CI workflow in
    `.github/workflows/ci.yml` exists, a small "markdown lint: passing"
    badge near the top is a low-key way to show the repo has automated
    checks, without needing a build or test badge that wouldn't make sense
    for a static file.

18. **Alt text on the stats image.** Line 111's image tag has alt text
    already (`Landon's GitHub stats`), which is good - worth keeping that
    habit for every image added from the ideas above, since profile READMEs
    are one of the more commonly screen-read pages on GitHub.
