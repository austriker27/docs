---
id: e100a366-b69c-4d59-bec7-eac18c0b286b
blueprint: modifiers
modifier_types:
  - string
  - array
  - utility
title: Raw
---
## Overview
Returns the [unaugmented](/augmentation) version of the variable.

## Example

If you had a Markdown field and wanted to render the actual Markdown-formatted text instead of rendered HTML, you can do this:

### The YAML
```yaml
markdown_field: >
  # How to Breakdance

  First you do the fancy kicky thing with your feets, and then
  you flail your legs around like a battery operated fan at a hot
  summer ballgame.
```

### The Template

::tabs

::tab antlers
```antlers
{{ markdown_field | raw }}
```
::tab blade
```blade
{{ $markdown_field->raw() }}
```
::

### The Output
```
# How to Breakdance

First you do the fancy kicky thing with your feets,
and then you flail your legs around like a battery
operated fan at a hot summer ballgame.
```
