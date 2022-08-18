I will collect some ideas for plugins that might be handy when
developing UFO:AI stuff.

## Plugins

- UFO Script Editor (ufo script and ump files)
  - UFO Script editor with basic syntax highlighing and outline is done
    [Scripteditors/EMFText‎](Scripteditors/EMFText‎ "wikilink")
  - started to work on a xtext based editor
- Model Viewer
  - md2 viewer basics are done - most of the models are not yet rendered
    corrctly though -
- GLSL Editor
  - glsl editors were forked to glshadereditor and must still be adpted
    to our needs
- Map compiler
- Tech tree editor
- Menu editor

## xtext based editor

### Prepare

- Install eclipse
- Install xtext 2.x (2.2.1) (Update site: )
- Import the net.sourceforge.ufoai.dsl\* projects (3) into your
  workspace

### Develop

- net.sourceforge.ufoai.dsl/src/UFOScript.xtext is the grammar file
  - right click - run as "generate xtext artifacts"
  - run the net.sourceforge.ufoai.dsl project as eclipse application.
    - import some ufoai ui scripts into your new workspace

### General

The java classes in net.sourceforge.ufoai.dsl/src and
net.sourceforge.ufoai.dsl.ui/src can get extended and won't get
overwritten. You can implement a formatter, validator and stuff like
that here.

### Links

- Hover support (inline dokumentation)
  -

  -

## Update site

## Links

-

-

-