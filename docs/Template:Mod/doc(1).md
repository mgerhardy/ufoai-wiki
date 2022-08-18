Implements the mathematical modulo operator. The returned result is
always of the same sign as the *modulus* or nul, and its absolute value
is lower than the absolute value of the *modulus*. However, this
template returns 0 if the *modulus* is nul (this template should never
return a division by zero error). This template is **not** the same as
the mod operator in the \#expr.

This template can be substituted.

## Usage


`{{mod|`*dividend*`|`*modulus*`}}`


Computes the modulo dynamically.

`{{subst:mod|`*dividend*`|`*modulus*`}}`


Substitute the template invokation by its computed value when saving an
article wiki source.

## Examples with positive integer modulus

- `{{mod|12|10}}` = .
- `{{mod|10.1|10}}` = .
- `{{mod|10|10}}` = .
- `{{mod|2|10}}` = .
- `{{mod|0|10}}` = .
- `{{mod|-2|10}}` = .
- `{{mod|-10|10}}` = .
- `{{mod|-10.1|10}}` = .
- `{{mod|-12|10}}` = .

## Examples with negative integer modulus

- `{{mod|12|-10}}` = .
- `{{mod|10.1|-10}}` = .
- `{{mod|10|-10}}` = .
- `{{mod|2|-10}}` = .
- `{{mod|0|-10}}` = .
- `{{mod|-2|-10}}` = .
- `{{mod|-10|-10}}` = .
- `{{mod|-10.1|-10}}` = .
- `{{mod|-12|-10}}` = .

## Examples with positive non integer modulus

- `{{mod|21.5|10.5}}` = .
- `{{mod|21.1|10.5}}` = .
- `{{mod|21|10.5}}` = .
- `{{mod|20.9|10.5}}` = .
- `{{mod|11|10.5}}` = .
- `{{mod|10.6|10.5}}` = .
- `{{mod|10.5|10.5}}` = .
- `{{mod|10.1|10.5}}` = .
- `{{mod|10|10.5}}` = .
- `{{mod|2|10.5}}` = .
- `{{mod|0|10.5}}` = .
- `{{mod|-2|10.5}}` = .
- `{{mod|-10|10.5}}` = .
- `{{mod|-10.1|10.5}}` = .
- `{{mod|-10.5|10.5}}` = .
- `{{mod|-10.6|10.5}}` = .
- `{{mod|-11|10.5}}` = .
- `{{mod|-20.9|10.5}}` = .
- `{{mod|-21|10.5}}` = .
- `{{mod|-21.1|10.5}}` = .
- `{{mod|-21.5|10.5}}` = .

## Examples with nul modulus

- `{{mod|2|0}}` = .
- `{{mod|0|0}}` = .
- `{{mod|-2|0}}` = .