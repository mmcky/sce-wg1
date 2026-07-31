# Archive

Superseded pages, kept for reference. Nothing here is published — the site is served from
[`docs/`](../docs/), and this directory is deliberately outside it.

| File | What it is |
| --- | --- |
| [`project-a-summary.html`](project-a-summary.html) | The hand-written Project A page as it stood at `2b4b410`, before the page was generated from [`project-a/special-issue-proposal.md`](../project-a/special-issue-proposal.md). |

## project-a-summary.html

An 810-word summary of the special-issue proposal, written for the site rather than extracted from
the proposal document. It organised the material into six numbered sections — Why, The proposal,
Domains of study, Research themes, Organization, and a link to the full document — with a card grid
for the four domains and a row list for the timeline.

It was replaced because the page and the document had begun to drift: the summary presented the
internal review step as settled, while the proposal marks it `[process TBC]`. Generating the page
from the markdown removes the second copy that has to be kept in step.

Worth keeping because the summary's *structure* may be useful again. If the group later wants a
short Project A landing page in front of the full proposal, this is the shape it took, and the
copy is reusable.

To view it, copy it into `docs/` — it links `chrome.css` and `chrome.js` relatively and will render
unstyled without them:

    cp archive/project-a-summary.html docs/_preview.html
    cd docs && python3 -m http.server
    # browse to localhost:8000/_preview.html, then delete the copy

Note the PDF link inside it points at a `github.com/.../blob/main/` URL, which was one of the
things the regenerated page fixed.
