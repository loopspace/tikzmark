# The tikzmark Package

This is the official home of the development repository for the
`tikzmark` library for LaTeX.
This package is for marking a position on a page or within a
`tikzpicture` which can be referred to in another TikZ drawing.

The current published version can be
found [on CTAN](https://ctan.org/pkg/tikzmark?lang=en) and the
documentation is there as a PDF.

To use the most recent version, download the file `tikzmark.dtx`.  To
generate the library files, run `tex tikzmark.dtx`.  To generate the
documentation, run `pdflatex tikzmark.dtx`.

## TL;DR

The `tikzmark` package provides a variety of commands which have
evolved over the years since I first defined it in 2009.  Much of this
has taken place on the [TeX-SX Q&A](https://tex.stackexchance.com)
([questions tagged
`tikzmark`](https://tex.stackexchange.com/questions/tagged/tikzmark)
and just [all posts mentioning `tikzmark`](https://tex.stackexchange.com/search?q=tikzmark))
site so there are many versions in answers on that site, and there
have been a few spin-offs by others.  There is much on that site that
is useful, but due to this evolution sometimes the command used by
older answers is not the right one when used with this library.

The main question to ask is: does the command make a node or just a
mark?
In brief, the _original_ `\tikzmark` made a node, but then I
simplified it to just make a mark.

### Marks

* `\tikzmark` - remembers a location on a page, can be used both
  inside and outside a `tikzpicture`, the position is available
  throughout the _entire_ document, including before it is defined.
* `\pgfmark` - a more basic location remembering command.
* `(pic cs:<name>)` - this is how to refer to a remembered mark in a
  `tikzpicture`.

### Nodes

* `\tikzmarknode` - creates a node around its contents, and remembers
  its location; uses some TeX trickery to detect math modes.
* `\subnode` - when used inside a TikZ node it creates a pseudo-node
  around its contents that can be used as if it were a node within the
  surrounding `tikzpicture`.

## Other Features

* Node saving: the marks created by `\tikzmark` and `\pgfmark` are
  available prior to their definition in the document; there is also
  facility for saving node information to make it available where it
  wouldn't normally - either earlier in the document or in a different
  document.
* Pic and scope positioning: nodes can be _anchored_ at certain
  locations, this extends that concept to pics and scopes.
  
### Additional Libraries

The concept of marking locations for TikZ has inspired a variety of
useful routines for particular situations, so are not loaded
automatically but can be accessed via `\usetikzmarklibrary`.  These
are:

* **listings**: for highlighting code listings when using the
  `listings` package.
* **ams**: puts a node around the boxes used by AMS math when it
  typesets equations.
* **higlighting**: simulates highlighting text delimited by a couple
  of tikzmarks.
