# Contributing

`awesome-agent-vault` is a category map. The bar for inclusion is real, the tone is neutral, and the maintainer (Authsome) does not get preferential placement. Read [CATEGORY-MAP.md](CATEGORY-MAP.md) before opening a PR.

## What can be added

- **Products** that vault, broker, or inject credentials for AI agents.
- **Integrations** that bridge a product to a specific agent platform (Claude Code, Codex, Cursor, etc.).
- **Service recipes** that describe the credential type and scopes for a third-party API when the consumer is an agent.
- **Patterns** that name a recurring problem and cite a project that demonstrably implements the solution.
- **Threat models** that document an attack surface with a citation (paper, blog post, real incident).

## What gets rejected

- Marketing copy. No "best-in-class", "revolutionary", "industry-leading". A custom linter rejects these and a long-standing list of similar adjectives.
- Vendor-only or self-promotional pages without working examples.
- Duplicates. A project belongs in exactly one category.
- Entries without verifiable links. Star counts and release dates carry a `last_verified` date.
- Em-dashes in entry prose. Use periods, commas, or middle dots.

## Entry shape

Every entry is one folder under the relevant top-level directory with a single `README.md`. Frontmatter is required:

```yaml
---
name: <display name>
slug: <kebab-case>
type: product | integration | service | pattern | threat-model
license: <SPDX identifier or "proprietary" or "n/a">
stars: <count or "n/a">
last_verified: 2026-05-27
maintainer: <github username or org>
related: [<list of other entry slugs>]
---
```

After the frontmatter, the body follows the per-type template in [.contributing/templates/](.contributing/templates/). Products: ~250 words. Integrations: ~250 words. Services: ~200 words. Patterns: ~300 words plus at least one citation. Threat models: ~300 words plus at least one citation.

## Verification

A PR can merge only if every applicable item is true:

1. The product, integration, or service entry contains a runnable example or a working configuration snippet. The contributor must have run it within the last 7 days.
2. Star counts and release dates carry a date. CI re-validates monthly via [scripts/refresh-metadata.js](scripts/refresh-metadata.js).
3. Pattern entries cite at least one production example with a link.
4. Threat model entries cite either a paper, a blog post, or a real incident with a link.
5. No marketing language. The lint job enforces this.

## PR template

```markdown
**Category:** product | integration | service | pattern | threat-model
**Entry slug:** kebab-case-name
**Maintainer relationship:** I maintain this project | I do not
**Last tested:** YYYY-MM-DD (must be within 7 days)
**Citations included:** yes | n/a

Checklist
- [ ] Frontmatter complete
- [ ] Body matches the per-type word count
- [ ] At least one link is reachable
- [ ] Read CATEGORY-MAP.md
- [ ] No em-dashes; no marketing adjectives
- [ ] If product/integration/service: runnable example or config snippet present
- [ ] If pattern: production-example citation
- [ ] If threat-model: paper or incident citation
```

## Neutrality

The maintainer of this list ships one of the products listed. When a PR adds a competitor, it is reviewed against the same checklist as every other entry. When a competitor improves their own entry, the PR is merged on the same terms.

If you believe an entry has been written unfairly (yours or someone else's), open an issue and link the entry. Vendor-review PRs are welcome and labeled `vendor-review`.

## Style

- Sentence case headings.
- One sentence summaries in `README.md` index. The folder `README.md` carries the long form.
- Cite primary sources (official docs). If a primary source does not exist, cite a third-party post and note the gap.
- No em-dashes. Period, comma, or middle dot.
- No exclamation marks.
- Adjectives are claims that must be backed by evidence.

## Licensing

Content is published under [CC0 1.0 Universal](LICENSE). By opening a PR you agree to release your contribution under the same terms.

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
