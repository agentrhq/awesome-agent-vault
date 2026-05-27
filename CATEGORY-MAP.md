# Category map, not a product page

`awesome-agent-vault` is a category map of the tooling that exists today for giving AI agents credentials safely. It is not a launch page, a comparison sheet weighted toward one vendor, or a funnel. It is a reference index, organized the way a working engineer would want to read it the first time they hit the problem.

The maintainer of this list, Authsome, is one of the projects listed inside it. That is disclosed in the maintainer footer of the README and nowhere else. It is not disclosed in the product rows, the compatibility matrix, the patterns section, or the threat model section, because in those sections the maintainer identity is not relevant. A reader scanning the list should not be able to guess which row the maintainer ships unless they already know.

Two non-negotiables follow from that, and they are stated up front so they can be checked.

First, every product is listed on equal terms regardless of maintainer. The same row schema applies to every entry: name, one-line scope, license, transport surface, language ecosystem, link. No row gets a star, a "featured" badge, a highlight color, or extra prose. The matrix cells use the same three states for every product. Alphabetical order is the only ordering inside each category. If a product belongs in a category, it is in that category, including direct competitors of the maintainer.

Second, the patterns section names whichever product best implements a pattern, not always the maintainer. A pattern entry is a short recipe ("rotating GitHub fine-grained tokens for a long-running agent", "scoping a Stripe restricted key to one customer"), and it cites the project that demonstrably handles that pattern best today, with a link to that project's own docs as evidence. Where the maintainer is genuinely best, it is cited. Where it is not, it is not. If a pattern has no clear best implementer, the pattern is described and no product is cited.

This document is the contract. Pull requests that violate either non-negotiable are out of scope, including pull requests from the maintainer.
