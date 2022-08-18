The EMFText script editor tries to provide an editor with syntax
highlighting, script code navigation and additional restriction checks.
It is based on [EMFText](http://www.emftext.org/index.php/EMFText),
which provides a framework to generate all needed files from a simple
syntax model.

As EMFText and UfoEditor are work in progress, there are some things
that have to receive attention: - As for now, we need the current trunk
version of EMFText, so see
[this](https://sourceforge.net/apps/trac/ufoai/browser/ufoai/eclipse/emftext.psf)
Team Project Set to check out and get the required plugins for extending
the UfoEditor plugins. You won't need those for just using the
plugins. - EMFText requires Eclipse EMF Feature - As EMFText has (known)
problems with duplicate keywords, some of the syntax scripts have to be
altered until EMFText provides a better solution (scannerless parsers)

## Usage

UfoEditor is automatically associated with \*.ufo files if the project
has the appropriate project nature.

## Overview

Model Plugin:

- model/ufo.ecore: Model for syntax elements
- model/ufo.genmodel: needed file for code generation
- model/ufo.cs: Main Syntax file, contains references to syntax modules
- model/ufo\*.cs: syntax modules for easier handling
- src/...: generated classes for model

Main Editor Plugin:

- src/...resource.ufo.analysis: reference resolvers
- src/...resource.ufo.analysis.finder: reuseable resolver stubs, rely on
  cache
- src/...resource.ufo.cache: current cache implementation, CacheAdder
  knows which values must be added to cache.

## Extend UfoEditor

Basically these steps are necessary to extend:

1.  make your changes to sub-cs file
2.  regenerate code for sub-cs file and main cs file
3.  for now: delete UfoPlugin from
    MainEditorPlugin/src-generated/...mopp, it gets overridden by
    generation, but original version is needed until better cache
    solution is found (EMFText Sokan is currently in evaluation)

## Additional Stuff

- additional post processors for syntax checks (e.g. correct path usage
  for icons/models) may be registered to UfoOptionProvider
- for now CacheAdder has to be extended if other objects have to be
  cached to be resolved later via cache

## Hints

- special token definitions used in sub-cs files must also be included
  in main cs file
- Choices won't be recognized without proper parenthesis around them, so
  don't forget to add them
- order of defines token definitions determines, which ones get higher
  priority

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")