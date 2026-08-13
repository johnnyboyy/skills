# skills — the constellation

An umbrella over four independently-tracked repos that form one system. Each child
keeps its own history, remote, and release cadence; this repo records **which commits
form a known-good constellation** — the versions proven green *together*.

| repo | owns |
|---|---|
| [praxis](praxis/) | the process engine — units, typed edges, gates, edit lease, journal, workflow packs |
| [corpora](corpora/) | the judgment lifecycle — compose, harvest, ratify / fold / distill, import / sync, reading |
| [domains](domains/) | the judgment itself — curated domain collections + provenance ledgers |
| [uiux](uiux/) | the design practice — library state, drift, deferred decisions, design workflows |

The four are version-coupled (corpora and uiux test against the sibling praxis checkout;
live roots wire the bucket's paths), which is why the umbrella pins SHAs rather than
tracking branches.

## Working in it

- **Day to day**: work in a child repo as usual — commit, push, ignore the umbrella.
- **Pin a constellation**: when the set is green together, from here:
  `git add praxis corpora domains uiux && git commit -m "constellation: <what changed>"`.
- **Fresh clone**: `git clone --recurse-submodules <this repo>`. Note: `corpora`,
  `domains`, and `uiux` have placeholder relative URLs until they get remotes — after
  publishing a child, run `git submodule set-url <name> <real-url>`.
- The children never "fall out": the umbrella tracks them as gitlinks + `.gitmodules`,
  never as plain directories.
