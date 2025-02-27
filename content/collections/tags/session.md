---
title: Session
description: 'Get, set, check, and forget data in your user''s session.'
intro: 'Sessions provide a stateless way to store information about the user across requests. The session tag will let you get, set, and forget session data.'
is_parent_tag: true
id: c15836c2-808d-4260-9d01-e5a569da5b5a
---
## Retrieving Session Data

You can use `{{ session }}` as a tag pair to access all the data inside your user's session.

::tabs

::tab antlers
```antlers
{{ session }}
    {{ message }}
{{ /session }}
```
::tab blade
```blade
<s:session>
  {{ $message }}
</s:session>
```
::

```.output
Welcome to the session.
```

You can also retrieve single variables with a single tag syntax.

::tabs

::tab antlers
```antlers
{{ session:message }}
```
::tab blade
```blade
{{-- Using Antlers Blade Components --}}
<s:session:message />

{{-- Using session() helper --}}
{{ session()->get('message') }}
```
::

## Setting and Forgetting

You can set data with [session:set](/tags/session-set), flash data with [session:flash](/tags/session-flash), forget it with [session:forget](/tags/session-forget), and flush the entire session with [session:flush](/tags/session-flush).

## Checking

You can check if data is set in a session with [session:has](/tags/session-has).

::tabs

::tab antlers
```antlers
{{ if {session:has key="has_voted"} === true }}
  You already voted. Thank you!
{{ /if }}
```
::tab blade
```blade
@if (session()->has('has_voted') === true)
  You already voted. Thank you!
@endif
```
::

## Debugging

If you want to peek into the session and check the data, do so with with [session:dump](/tags/session-dump) or the [debug bar](/debugging#debug-bar).

## Aliasing

If you need extra markup around your session data, you can _alias_ a new child array variable.

::tabs

::tab antlers
```antlers
{{ session as="sesh" }}
  {{ sesh }}
    {{ message }}
  {{ /sesh }}
{{ /session }}
```
::tab blade
```blade
{{-- Using the session() helper and PHP --}}
@php($sesh = session()->all())
```
::

