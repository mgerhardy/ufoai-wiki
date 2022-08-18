This script file allows you to define categories for notify types. These
categories are used to group settings for those types.

Every line in a msgcategory definition contains one notify type (as
defined in nt_strings in )

    msgcategory "_install_equipment" {
        installation_installed
        installation_removed
        installation_replaced
    }

- category names should include no whitespace and must be marked
  translateable (by surrounding them with
  <b>"_</b><category_name><b>"</b>)
- each notify type should occur only in one category
- definition order in defines order visible in options menu

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")