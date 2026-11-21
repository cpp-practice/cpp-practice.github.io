# Design

## Context

The site is plain HTML and CSS published as a static GitHub Pages repository. It currently has a generic `index.html`, shared `styles.css`, and one self-contained lecture deck at `lecs/lec-01-08.html`. See proposal.md for motivation and specs/course-site/spec.md for observable requirements.

## Goals / Non-Goals

**Goals:**
- Use the existing static hosting and file layout.
- Keep the lecture catalog easy to extend by adding another hardcoded entry.
- Let the URL identify the selected lecture and support browser history.
- Present a usable split layout on both desktop and narrow screens.

**Non-Goals:**
- Automatic discovery or generation of lecture entries.
- Changes to lecture deck content or generation pipeline.
- Accounts, server-side state, progress tracking, or a course management system.

## Decisions

- Keep the catalog markup in `lectures.html`. The current catalog has one item, and a manually maintained list matches the requested workflow without introducing a build step.
- Use a fragment identifier based on a stable lecture key, such as `#lec-01-08`, to select entries. A small vanilla JavaScript handler maps each key to its `data-src`, updates the iframe and active item, and listens to `hashchange`; this supports direct links and browser back/forward without a server.
- Load the existing self-contained deck in an iframe. Do not sandbox it because the generated presentation may need its own scripts and browser presentation controls.
- Use a two-column CSS grid on wide screens. On narrow screens, stack the list above the frame and constrain the viewer area to the available viewport; provide an open-in-new-tab link for the selected deck for devices where embedded slides are awkward.
- Share `styles.css` between the landing page and viewer, using page-specific classes to avoid coupling their layouts.
- Keep shell interface copy in English, consistent with the existing `index.html`; the lecture deck's original language and content remain unchanged.

Alternatives considered: an automatically generated manifest would require a build step or server-side directory listing unavailable to browser code on static hosting; separate pages per lecture would duplicate viewer chrome and make switching less direct.

## Risks / Trade-offs

- [A hardcoded catalog can become stale when lecture files are renamed] -> Keep each item's stable key and relative source together in one markup entry and document that adding a lecture means adding an entry.
- [An iframe may be constrained on small screens] -> Stack the layout and expose the selected source as an open-in-new-tab link.
- [A malformed or unknown URL fragment may not map to a lecture] -> Fall back to the first listed lecture and normalize the fragment to its key.

## Migration Plan

Replace the generic homepage, add the viewer page and selection behavior, then publish the static files as usual. Rollback consists of restoring the prior homepage and stylesheet and removing the viewer page/script; lecture files are unaffected.
