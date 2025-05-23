---
id: e6fdbeb6-7808-45b0-b012-89a34993778b
blueprint: variables
types:
  - system
title: Site
---
The current site being targeted in the request.

It's a `Statamic\Sites\Site` object and can be used as a single tag or tag pair.

``` php
// config/statamic/sites.php

'sites' => [
    'default' => [
        'name' => 'My Statamic Site',
        'locale' => 'en_US',
        'url' => '/',
        'direction' => 'ltr',
        'attributes' => [
            'foo' => 'bar',
        ],
    ]
]
```

As a single tag, it will output the handle of the site:

::tabs

::tab antlers
```antlers
{{ site }}
```
::tab blade
```blade
{{ $site }}
```
::

```html
default
```

As a tag pair, you can access additional information:

::tabs

::tab antlers
```antlers
{{ site }}
    {{ handle }}
    {{ name }}
    {{ locale }}
    {{ short_locale }}
    {{ url }}
    {{ permalink }}
    {{ direction }}
    {{ attributes }}
        {{ foo }}
    {{ /attributes }}
{{ /site }}
```
::tab blade
```blade
{{ $site->handle }}
{{ $site->name }}
{{ $site->locale }}
{{ $site->short_locale }}
{{ $site->url }}
{{ $site->permalink }}
{{ $site->direction }}

{{ $site->attributes['foo'] }}
```
::

```html
default
My Statamic Site
en_US
en
/
http://mysite.com/
ltr
bar
```

You can also access those variables directly as single tags:

::tabs

::tab antlers
```antlers
{{ site:name }}
{{ site:attributes:foo }}
```
::tab blade
```blade
{{ $site->name }}
{{ $site->attributes['foo'] }}
```
::

```html
My Statamic Site
bar
```
