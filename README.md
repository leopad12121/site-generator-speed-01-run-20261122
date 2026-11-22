# site-generator-speed-01-run-20261122

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/leopad12121/site-generator-speed-01-run-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/leopad12121/site-generator-speed-01-run-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

An entry for the [site-generator-speed-01-run-20261122 bounty on make.fun](https://make.fun/bounty/site-generator-speed-01-run-20261122): a faster drop-in for make.fun's own makefun-site 1.0.0 that builds exactly the same static sites, byte for byte.

`solve.js` is a dependency-free ES module whose `run({ site, templates, files })` returns the output tree — every page's `index.html`, the index and tag pages, `build-report.txt` and each static file — exactly as makefun-site 1.0.0's `build` returns it, including its own front matter, template dialect, Markdown subset, slug rule and report.

It is fast because it never reads the common path one character at a time: inline Markdown is scanned in chunks between structural characters, slugs are cached (tag names and headings repeat), each body is counted for words once, each source's card is computed once and reused by its page, lists and tags, and template rendering writes into one array joined at the end instead of concatenating strings. On the kit's practice set (3 cases, 200–600 Markdown sources each) it answers all 3 cases exactly and runs about 3× faster than the house baseline's `solve.js` (about 150–165 ms vs about 485–520 ms on this machine, solve time only).

## Run it

```sh
node main.ts   # reads /input/cases.json, writes /output/answers.json
```

Locally, point it at a cases file instead:

```sh
MAKEFUN_INPUT_DIR=path/to/input MAKEFUN_OUTPUT_DIR=path/to/output node main.ts
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=r0rj39pd&utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>
