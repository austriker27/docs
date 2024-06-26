---
id: bbea4454-efa2-4372-842b-b295376230f7
blueprint: repositories
title: 'Form Repository'
nav_title: Forms
related_entries:
  - fdb45b84-3568-437d-84f7-e3c93b6da3e6
  - e4f4f91e-a442-4e15-9e16-3b9880a25522
  - d630ea15-d94f-4404-84d2-0926a898e672
  - 02261135-24fa-4d2f-9bc5-a7d2f5e6a975
---
To work with the Form Repository, use the following Facade:

```php
use Statamic\Facades\Form;
```

## Methods

| Methods | Description |
| ------- | ----------- |
| `all()` | Get all Forms |
| `find($handle)` | Get Form by `handle` |
| `findOrFail($handle)` | Get Form by `handle`. Throws a `FormNotFoundException` when the form cannot be found. |
| `make()` | Makes a new `Form` instance |

:::tip
The `handle` is the name of the form's YAML file.
:::

## Querying

#### Examples {.popout}

#### Get a single form by its handle

```php
Form::find('postbox');
```

When a form can't be found, the `Form::find()` method will return `null`. If you'd prefer an exception be thrown, you may use the `findOrFail` method:

```php
Form::findOrFail('postbox');
```

#### Get all forms from your site

```php
Form::all()
```

#### Get submissions to a form by its handle

```php
Form::find('postbox')->submissions();
```

The `->submissions()` method will return a `Collection` of form submissions. You can use the [Form Submissions repository](/repositories/form-submission-repository) if you need to query form submissions further.

#### Get the blueprint of a form

```php
Form::find('postbox')->blueprint();
```


## Creating

Start by making an instance of a form with the `make` method.
You need at least a handle before you can save a form.

```php
$form = Form::make()->handle('feedback');
```

You may call additional methods on the entry to customize it further.

```php
$form
  ->handle('postbox')
  ->honeypot('winnie-the-pooh')
  ->title('The Hundred Acre Wood');
```

Finally, save it. It'll return a boolean for whether it succeeded.

```php
$form->save(); // true or false
```
