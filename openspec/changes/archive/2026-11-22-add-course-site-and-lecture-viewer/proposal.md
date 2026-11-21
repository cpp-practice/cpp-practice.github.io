# Proposal

## Why

The repository contains lecture slides but its homepage is generic and gives students no clear course entry point. A course landing page and a dedicated viewer will make the existing lecture accessible while leaving room to add more hardcoded entries later.

## What Changes

- Replace the generic homepage with a course presentation and a clear link to the lecture viewer.
- Add `lectures.html` with a vertical split: a lecture list on the left and a frame displaying the selected HTML deck on the right.
- Hardcode the current single lecture in the list, with its title and path under `lecs/`.
- Make the selected lecture addressable and navigable through the URL, and adapt the layout for narrow screens.

## Capabilities

### New Capabilities

- `course-site`: Course landing page and lecture viewer behavior for presenting existing HTML lecture decks.

### Modified Capabilities

None.

## Impact

- Affected files: `index.html`, new `lectures.html`, and `styles.css`; a small script may be added for selecting lectures and synchronizing URL state.
- Existing deck `lecs/lec-01-08.html` is embedded directly and remains the lecture content source.
- No backend, build system, or external dependencies are required.
