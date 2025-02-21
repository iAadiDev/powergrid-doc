# Table Rows

This section covers the Table Row features.

Here you will find:

[[toc]]

## Checkboxes

To enable checkboxes on Table rows, call the `showCheckBox()` in your Component's `setUp()` method.

By default, `showCheckBox()` reference the field `id`. If you need to reference another field, simply pass the field name to the parameter `$attribute`.

Example:

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;

class DishTable extends PowerGridComponent
{
    public function setUp(): array
    {
        $this->showCheckBox();// [!code ++]
    }
}
```

<div class="onlinedemo custom-block">
  <p class="custom-block-title">🚀 See it in action</p>
  <p>See an interactive example using <a target="_blank" href="https://demo.livewire-powergrid.com/examples/input-checkbox">Checkboxes</a> on a Table.</p>

</div>

## Radio Buttons

To enable radio buttons on Table rows, call the `showRadioButton()` in your Component's `setUp()` method.

By default, `showRadioButton()` reference the field `id`. If you need to reference another field, simply pass the field name to the parameter `$attribute`.

Example:

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;

class DishTable extends PowerGridComponent
{
    public function setUp(): array
    {
        $this->showRadioButton();// [!code ++]
    }
}
```

<div class="onlinedemo custom-block">
  <p class="custom-block-title">🚀 See it in action</p>
  <p>See an interactive example using <a target="_blank" href="https://demo.livewire-powergrid.com/examples/input-checkbox">Radio Buttons</a> on a Table.</p>

</div>

## Dropdown Menu

See Formatting Data [Dropdown Menu](/table-component/data-source-fields.html#dropdown-menu).

## Inline Editing

See [Edit On Click](/table-features/columns.html#edit-on-click).

## Toggle Switch

See [Toggleable](/table-features/columns.html#toggleable).

## Buttons

Buttons are registered inside the method [`actions()`](/table-component/component-configuration.html#actions-method) in your Table Component class.

Inside this method, you have access to the (`Model`|`array`) `$row` variable containing the rendered row's data.

To add buttons to each row, you must add a call to [Buttons::class](/table-features/button-class.html), and proceed chaining as many [Button methods](/table-features/button-class.html#button-methods) as you need.

In addition, make sure you have added an [Action Column](/table-features/columns.html#action-column) to your Component.

The example below creates a button to dispatch an event when clicked.

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;
use PowerComponents\LivewirePowerGrid\Button;

class DishTable extends PowerGridComponent
{
    public function actions($row): array
    {
        return [
            Button::add('edit-stock')// [!code ++:4]
                ->slot("Edit <strong>{e($row->name)}</strong>")
                ->class('bg-indigo-500 text-white')
                ->dispatch('clickToEdit', ['dishId' => $row->id]),
        ];
    }
}
```

<div class="onlinedemo custom-block">
  <p class="custom-block-title">🚀 See it in action</p>
  <p>See an interactive example using <a target="_blank" href="https://demo.livewire-powergrid.com/examples/input-button">Buttons</a> on a Table.</p>

</div>

## Actions From Blade View

PowerGrid offers the possibility to render a custom view inside each row's [Action Column](/table-features/columns.html#action-column).

This is useful when you need to build a combination of actions for a complex scenario or when working with cache on a large dataset.

To load actions from a View, add a method `actionsFromView()` to your PowerGrid Component returning a `View`.

Inside this method, you have access to the (`Model`|`array`) `$row` variable containing the rendered row's data.

Example:

```php
use Illuminate\View\View;

public function actionsFromView($row): View
{
    return view('actions-view', ['row' => $row]);
}
```

Your view may look something like the example below.

```php
// resources/views/actions-view.blade.php

<div>
    @if($row->in_stock == 'Yes')
        <button>Order now</button>
    @else
        - out of sock -
    @endif
</div>
```

<div class="onlinedemo custom-block">
  <p class="custom-block-title">🚀 See it in action</p>
  <p>See an interactive example using <a target="_blank" href="https://demo.livewire-powergrid.com/examples/actions-from-view">Action From View</a>.</p>

</div>

## Image in Cell

See Formatting Data [Image](/table-component/data-source-fields.html#image).

## Cell Data Formatting

See [Custom Fields](/table-component/data-source-fields.html#custom-fields) and [Formatting Data Examples](/table-component/data-source-fields.html#formatting-data-examples).

## Conditionally Show/Hide Controls

See [Conditional Rules](/table-features/conditional-rules.html).

## Collapsible Rows

See [Detail Row](/table-component/component-configuration.html#detail-row).

## Multi-row Bulk Actions

See [Bulk Actions](/table-features/bulk-actions.html).
