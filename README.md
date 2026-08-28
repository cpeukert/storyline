# storyline

**storyline** is a small, dependency-free editor for rearranging the structure of a LaTeX document. Paste a document, visualize its headings as a tree, move or edit them, and copy the updated LaTeX.

Live version: [storyline.acadmc.com](https://storyline.acadmc.com)

## Features

- Parses a complete LaTeX document into a visual outline.
- Supports `\part`, `\chapter`, `\section`, `\subsection`, `\subsubsection`, `\paragraph`, and `\subparagraph`.
- Moves headings together with their text and descendants.
- Reorders and nests branches with mouse drag-and-drop.
- Collapses and expands lower hierarchy levels.
- Edits heading titles directly in the tree.
- Adds sections from the root and child headings from each element's `+` button.
- Supports undo and redo.
- Copies the regenerated LaTeX with one button.
- Runs entirely in the browser; documents are not uploaded anywhere.

## Run locally

No installation or build step is required. Clone the repository and open `index.html` in a modern desktop browser.

```bash
git clone https://github.com/cpeukert/storyline.git
cd storyline
open index.html
```

Alternatively, serve the directory with any static file server:

```bash
python3 -m http.server 4173
```

Then open [http://localhost:4173](http://localhost:4173).

## Usage

1. Paste LaTeX into **Step 1** and select **Build tree**.
2. In **Step 2**:
   - Drag a handle above or below another heading to reorder it.
   - Drop a heading in the center of another heading to nest it.
   - Select a title to edit it.
   - Use the arrow to collapse or expand descendants.
   - Use `+` to add a child one hierarchy level lower.
   - Use **Add section** to append a new section.
3. Select **Copy LaTeX** and paste the result into your editor.

## How source is preserved

Text between two headings belongs to the preceding heading. Moving a heading therefore moves its prose, labels, figures, equations, comments, and descendants as one branch. The preamble remains fixed, and `\end{document}` remains at the end.

Supported documents round-trip without structural edits: stars, optional short titles, whitespace, title markup, and non-heading content remain intact.

## Parser scope

storyline is a structural scanner, not a TeX engine. It ignores commented-out headings and headings inside common verbatim-style environments. It does not expand custom macros, evaluate conditionals, or follow `\input` and `\include` files. Malformed heading commands are left unchanged and reported as warnings.

## Project structure

The complete application—HTML, CSS, and JavaScript—lives in [`index.html`](index.html). There are no packages, external assets, or runtime dependencies.
