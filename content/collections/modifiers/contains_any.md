---
id: 20ac3e9a-4a45-4c2f-9052-be222fc84016
blueprint: modifiers
modifier_types:
  - conditions
title: 'Contains Any'
---
Search a string against multiple needles and return `true` if any are found, otherwise `false`. Case-insensitive.

```yaml
summary: "It was the best of times, it was the worst of times."
```

::tabs

::tab antlers
```antlers
{{ if summary | contains_any('good', 'better', 'best') }}
```
::tab blade
```blade
@if (Statamic::modify($summary)->containsAny(['good', 'better', 'best'])->fetch()) @endif
```
::

```html
true
```
