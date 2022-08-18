This template generates a pseudo-random integer between 0 and *count*-1.

## Usage

- `{{Rand|`*count*`|`*seed*`|`*prime*`}}`
- All parameters are optional and have default values. They must be
  integers.
- The default *count* is 100 (so by default, this template generates
  values between 0 and 99) and must be non-zero.
- The default *seed* is {{#time:z}} and can be set to any other integer
  value (used to generate distinct values on the same page).
- The default *prime* is 67 and should be a prime number above 17 (used
  to generate distinct values on the same page).

## Examples generating numbers between 0 and 999

- `{{Rand|1000}}` =
- `{{Rand|1000|{{#time:z}}|67}}` = \|67}} (same as above)
- `{{Rand|1000|{{#time:z}}|61}}` = \|61}} (this and others should all be
  different)
- `{{Rand|1000|6}}` =
- `{{Rand|1000|5}}` =
- `{{Rand|1000|4}}` =
- `{{Rand|1000|3}}` =
- `{{Rand|1000|2}}` =
- `{{Rand|1000|1}}` =
- `{{Rand|1000|0}}` =
- `{{Rand|1000|1|17}}` = (varying the prime number)
- `{{Rand|1000|1|19}}` =
- `{{Rand|1000|1|23}}` =
- `{{Rand|1000|1|29}}` =
- `{{Rand|1000|1|31}}` =
- `{{Rand|1000|1|37}}` =
- `{{Rand|1000|1|41}}` =
- `{{Rand|1000|1|43}}` =
- `{{Rand|1000|1|47}}` =
- `{{Rand|1000|1|51}}` =
- `{{Rand|1000|1|53}}` =
- `{{Rand|1000|1|59}}` =
- `{{Rand|1000|1|61}}` =
- `{{Rand|1000|1|67}}` =
- `{{Rand|1000|1|71}}` =
- `{{Rand|1000|1|73}}` =
- `{{Rand|1000|1|79}}` =

## Note

- Varying *seed* linearly generates numbers that generate a linear
  sequence on the same page, with equal cyclic steps;
- Varying *prime* (provided that they are odd prime numbers) generates
  pseudo-random that have independent random distribution.
- Note that when *count* is even (such as 100 by default, or 1000 in the
  examples above), the generated numbers (on the same page) are all odd
  or all even when you are varying the *seed* or *prime*, unless half of
  the calls use an even *seed* and the others used an odd *seed*.
  However, later invokations will still alternate odd and even numbers
  on output (this problem only occurs on the same page where multiple
  random numbers are invoked).
- On the same page, multiple invokations of this template with the same
  parameters will generate the same output value, so it is possible to
  create multiple links related to the same article.