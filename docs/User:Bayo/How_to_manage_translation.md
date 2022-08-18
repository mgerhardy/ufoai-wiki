## How to add a new translation language

- Edit the template [Template:Translation
  subpages](Template:Translation_subpages "wikilink")
  - Copy-paste an entry and edit it to the new language.
  - This template is used to generate expected links, e.g.
    [Translation:Default_pre_txt](Translation:Default_pre_txt "wikilink")
- Create a page like [List of msgid/en](List_of_msgid/en "wikilink")
  with the expected code
  - `{{Translation msgids|lang=CODE}}`
  - Replace `CODE` with the language code.

## How to add a new translation entry

- Create a page name with `Translation:` prefix.
  - e.g.
    [Translation:Default_pre_txt](Translation:Default_pre_txt "wikilink")
- Initialize this page with the code `{{Translation subpages}}`.
  - The use of this template will create links for all expected
    languages.
- Edit the template [Template:Translation
  msgids](Template:Translation_msgids "wikilink") to add your new entry.
  - e.g. add
    `{{Template:Translation msgids/entry|msgid=default_pre_txt|lang={{{lang}}}}}`
  - This template is used to generate pages like [List of
    msgid/en](List_of_msgid/en "wikilink")