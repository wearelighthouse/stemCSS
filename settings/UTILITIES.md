# Utilities
- Lists of property: value;
- We have three types:

## Simple Values
Just a list of `value` (optional: class)

## Placeholders
Generate a `%placeholder` (optional: class)

## Complex Values
A Value that can have:
- `value` required
- `pseudos` optional
- `breakpoints` optional
- `combinator` optional

## Stepped Values
A number or unit that is looped to create utilities:
- `start` number, required
- `end` number, required
- `step` optional, +integer to loop over
- `unit` optional

```
$utilities-property-settings: (
  (
    // Property
    property: margin,
    property: ('margin', 'm'),
    property: (('margin-left', 'margin-right'), 'mh'),

    values: (
      // Simple Values
      (
        auto,
        ('auto', 'au'),
      ),

      // Placeholders
      (
        0,
        ('inherit', 'inh'),
      ),

      // Complex Values
      (
        value: ('2rem', '2'),
        pseudos: (visited, ('hover', 'focus')),
        breakpoints: ('uptolarge', 'fromlarge'),
        combinator: ('> *', 'child'),
      ),

      // Stepped Values
      (
        start: -10,
        end: 50,
        step: 10,
        unit: ('%', 'pc'),
      ),
    ),
  ),
);

$make-utilities: append($make-utilities, $utilities-property-settings);
```