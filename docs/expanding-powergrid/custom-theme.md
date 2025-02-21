# Custom Theme

This section covers PowerGrid Custom Themes.

Here you will find:

[[toc]]

## Introduction

You can start customizing the [default themes](/get-started/powergrid-configuration.html#_2-choose-a-css-theme) to create your own variation in a few steps.

You may also have a look at the [Personalizing Header and Footer](/table-features/header-and-footer.html#personalizing-header-footer) subsection before creating a new theme.

## Creating your Custom Theme

To create your Custom Theme, first [install](/get-started/install) PowerGrid and then, follow the steps below.

1. Open the directory `vendor/power-components/livewire-powergrid/src/Themes/`

2. Copy the theme you want to use as base (`Tailwind.php`  or `Bootstrap5.php` ) to the directory where you want  you theme to live (for example `app\PowerGridThemes\BigFonts.php`).

3. Now, modify the `namespace`,  `class name` and customize the css to your needs.

The example below modifies the Tailwind theme:

```php
<?php

namespace App\PowerGridThemes;

use \PowerComponents\LivewirePowerGrid\Themes\Tailwind;
use \PowerComponents\LivewirePowerGrid\Themes\Theme;
use PowerComponents\LivewirePowerGrid\Themes\Components\{Actions, Checkbox, ClickToCopy, Cols, Editable, FilterBoolean, FilterDatePicker, FilterInputText, FilterMultiSelect, FilterNumber, FilterSelect, Footer, Table};

class BigFonts extends Tailwind
{
    public string $name = 'tailwind';

    public function table(): Table
    {
        return Theme::table('rounded-lg min-w-full border border-slate-200 dark:bg-slate-600 dark:border-slate-500')
            ->div('my-3 overflow-x-auto bg-white shadow-lg rounded-lg overflow-y-auto relative')
            ->thead('shadow-sm bg-slate-100 dark:bg-slate-800 border border-slate-200 dark:border-slate-500')
            ->thAction('!font-bold text-right')
            ->tdAction('')
            ->tr('')
            ->trFilters('bg-white shadow-sm dark:bg-slate-700')
            ->th('font-semibold px-2 pr-4 py-3 text-left text-xl font-semibold text-slate-700 tracking-wider whitespace-nowrap dark:text-slate-300')
            ->tbody('text-slate-800')
            ->trBody('border border-slate-100 dark:border-slate-400 hover:bg-slate-50 dark:bg-slate-700 dark:odd:bg-slate-800 dark:odd:hover:bg-slate-900 dark:hover:bg-slate-700')
            ->tdBody('px-3 py-2 whitespace-nowrap dark:text-slate-200')
            ->tdBodyTotalColumns('px-3 py-2 whitespace-nowrap dark:text-slate-200 text-sm text-slate-600 text-right space-y-2');
    }

    public function footer(): Footer
    {
        return Theme::footer()
            ->view($this->root() . '.footer')
            ->select('block appearance-none bg-slate-50 border border-slate-300 text-slate-700 py-2 px-3 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-slate-500  dark:bg-slate-600 dark:text-slate-200 dark:placeholder-slate-200 dark:border-slate-500');
    }

    public function actions(): Actions
    {
        return Theme::actions()
            ->headerBtn('block w-full bg-slate-50 text-slate-700 border border-slate-200 rounded py-2 px-3 leading-tight focus:outline-none focus:bg-white focus:border-slate-600 dark:border-slate-500 dark:bg-slate-600 2xl:dark:placeholder-slate-300 dark:text-slate-200 dark:text-slate-300')
            ->rowsBtn('focus:outline-none text-sm py-2.5 px-5 rounded border');
    }

    public function cols(): Cols
    {
        return Theme::cols()
            ->div('')
            ->clearFilter('', '');
    }

    public function editable(): Editable
    {
        return Theme::editable()
            ->view($this->root() . '.editable')
            ->span('flex justify-between')
            ->input('dark:bg-slate-700 bg-slate-50 text-black-700 border border-slate-400 rounded py-2 px-3 leading-tight focus:outline-none focus:bg-white focus:border-slate-500 dark:bg-slate-600 dark:text-slate-200 dark:placeholder-slate-200 dark:border-slate-500 p-2');
    }

    public function clickToCopy(): ClickToCopy
    {
        return Theme::clickToCopy()
            ->span('flex justify-between');
    }

    public function checkbox(): Checkbox
    {
        return Theme::checkbox()
            ->th('px-6 py-3 text-left text-xs font-medium text-slate-500 tracking-wider')
            ->label('flex items-center space-x-3')
            ->input('h-4 w-4');
    }

    public function filterBoolean(): FilterBoolean
    {
        return Theme::filterBoolean()
            ->view($this->root() . '.filters.boolean')
            ->base('min-w-[5rem]')
            ->select('appearance-none block mt-1 mb-1 bg-white border border-slate-300 text-slate-700 py-2 px-3 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-slate-500 w-full active dark:bg-slate-600 dark:text-slate-200 dark:placeholder-slate-200 dark:border-slate-500', 'max-width: 370px');
    }

    public function filterDatePicker(): FilterDatePicker
    {
        return Theme::filterDatePicker()
            ->base('p-2')
            ->view($this->root() . '.filters.date-picker')
            ->input('flatpickr flatpickr-input block my-1 bg-white border border-slate-300 text-slate-700 py-2 px-3 rounded leading-tight focus:outline-none focus:bg-white focus:border-slate-500 w-full active dark:bg-slate-600 dark:text-slate-200 dark:placeholder-slate-200 dark:border-slate-500', 'min-width: 12rem');
    }

    public function filterMultiSelect(): FilterMultiSelect
    {
        return Theme::filterMultiSelect()
            ->base('inline-block relative w-full p-2 min-w-[180px]')
            ->view($this->root() . '.filters.multi-select');
    }

    public function filterNumber(): FilterNumber
    {
        return Theme::filterNumber()
            ->view($this->root() . '.filters.number')
            ->input('block bg-white border border-slate-300 text-slate-700 py-2 px-3 rounded leading-tight focus:outline-none focus:bg-white focus:border-slate-500 w-full active dark:bg-slate-600 dark:text-slate-200 dark:placeholder-slate-200 dark:border-slate-500 min-w-[5rem]');
    }

    public function filterSelect(): FilterSelect
    {
        return Theme::filterSelect()
            ->view($this->root() . '.filters.select')
            ->base('min-w-[9.5rem]')
            ->select('appearance-none block bg-white border border-slate-300 text-slate-700 py-2 px-3 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-slate-500 w-full active dark:bg-slate-600 dark:text-slate-200 dark:placeholder-slate-200 dark:border-slate-500');
    }

    public function filterInputText(): FilterInputText
    {
        return Theme::filterInputText()
            ->view($this->root() . '.filters.input-text')
            ->base('min-w-[9.5rem]')
            ->select('appearance-none block bg-white border border-slate-300 text-slate-700 py-2 px-3 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-slate-500 w-full active dark:bg-slate-600 dark:text-slate-200 dark:placeholder-slate-200 dark:border-slate-500')
            ->input('w-full block bg-white text-slate-700 border border-slate-300 rounded py-2 px-3 leading-tight focus:outline-none focus:bg-white focus:border-slate-500 dark:bg-slate-600 dark:text-slate-200 dark:placeholder-slate-200 dark:border-slate-500');
    }
}
```

4. Finally, you can [configure](/get-started/powergrid-configuration.html#_2-choose-a-css-theme) PowerGrid to use your new theme:

```php{10}
// config/livewire-powergrid.php

/*
|--------------------------------------------------------------------------
| Theme
|--------------------------------------------------------------------------
*/

'theme' => \PowerComponents\LivewirePowerGrid\Themes\Tailwind::class, // [!code --]
'theme' => \App\PowerGridThemes\BigFonts::class, // [!code ++]
```




Alternatively, you can apply your custom theme only in specific PowerGrid Tables:

Just modify the `template()` to return your new theme class.

```php
class DishTable extends PowerGridComponent
{
    public function template(): ?string
    {
        return \App\PowerGridThemes\BigFonts::class;
    }```
