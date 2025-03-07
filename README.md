# Filament Advanced Components

This plugin extends existing **FilamentPHP 3** components with advanced features and enhanced functionality, offering more powerful and flexible options for your projects.

> [!NOTE]  
> All components are extending the default Filament components, so you can use them as you would use the default components without any issues. This package is designed to enhance the default components, not to replace them.

## Licences
You can buy a license for the plugin on the [AnyStack](https://checkout.anystack.sh/filament-advanced-components) website for $59.99. This is a lifetime license, which means you only need to pay once and the best part is that you can use it on multiple projects.

## Installation

To install the plugin, you need to add the repository to your composer.json file. You can do this by running the following command:

```json
{
    "repositories": [
        {
            "type": "composer",
            "url": "https://filament-advanced-components.composer.sh"
        }
    ]
}
```

Once the repository has been added to the composer.json file, you can install Filament Advanced Components like any other composer package using the composer require command:

```bash
composer require codewithdennis/filament-advanced-components
```

You will be prompted to provide your username and password. The username will be the email address and the password will be equal to your license key.

```bash
Loading composer repositories with package information
Authentication required (filament-advanced-components.composer.sh):
Username: [licensee-email]
Password: [license-key]
```

### Custom Theme
You will need a [custom theme](https://filamentphp.com/docs/3.x/panels/themes#creating-a-custom-theme) to use the plugin.

Make sure you add the following to your `tailwind.config.js file.

```bash
'./vendor/codewithdennis/filament-advanced-components/resources/**/*.blade.php',
```

Include the following import in your theme stylesheet.

```css
@import '/vendor/codewithdennis/filament-advanced-components/resources/css/index.css';
```

## AdvancedCheckboxList

### Suffix image

You can add an image as a suffix to the text column. The image will be displayed on the right side of the text column.

```php
AdvancedCheckboxList::make('country.name')
    ->relationship('country', 'name')
    ->suffixImage(fn (Country $record) => asset('images/'.$record->image))
    ->suffixImageSize(32)
    ->suffixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

### Prefix image

You can add an image as a prefix to the text column. The image will be displayed on the left side of the text column.

```php
AdvancedCheckboxList::make('country.name')
    ->relationship('country', 'name')
    ->prefixImage(fn (Country $record) => asset('images/'.$record->image))
    ->prefixImageSize(32)
    ->prefixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

## AdvancedSelect

### Suffix image

You can add an image as a suffix to the text column. The image will be displayed on the right side of the text column.

```php
AdvancedSelect::make('country.name')
    ->relationship('country', 'name')
    ->suffixImage(fn (Country $record) => asset('images/'.$record->image))
    ->suffixImageSize(32)
    ->suffixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

### Prefix image

You can add an image as a prefix to the text column. The image will be displayed on the left side of the text column.

![advanced-select](https://raw.githubusercontent.com/CodeWithDennis/filament-advanced-components-documentation/refs/heads/main/art/advanced-select.png)

```php
AdvancedSelect::make('country.name')
    ->relationship('country', 'name')
    ->prefixImage(fn (Country $record) => asset('images/'.$record->image))
    ->prefixImageSize(32)
    ->prefixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

## AdvancedTextEntry

### Suffix image

You can add an image as a suffix to the text column. The image will be displayed on the right side of the text column.

```php
AdvancedTextEntry::make('country.name')
    ->suffixImage(fn (Country $record) => asset('images/'.$record->image))
    ->suffixImageSize(16)
    ->suffixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

### Prefix image

You can add an image as a prefix to the text column. The image will be displayed on the left side of the text column.

```php
AdvancedTextEntry::make('country.name')
    ->prefixImage(fn (Country $record) => asset('images/'.$record->image))
    ->prefixImageSize(16)
    ->prefixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

### Mailable

You can make the text column mailable. When clicked, it will open the default email client with the state value.

```php
AdvancedTextEntry::make('email')
    ->mailable()
```

If you want to apply a mailable based on a condition, you can pass a closure that returns a boolean value.

```php
AdvancedTextEntry::make('email')
    ->mailable(fn (string $state) => str($state)->endsWith('.com'))
```

### Callable

A simple way to make a value clickable and open the default phone client with the phone number.

```php
AdvancedTextEntry::make('phone')
    ->callable()
```

If you want to apply a callable based on a condition, you can pass a closure that returns a boolean value.

```php
AdvancedTextEntry::make('phone')
    ->callable(fn (string $state) => str($state)->startsWith('+')),
```

### WhatsApp-able

A simple way to make a value clickable and open the default WhatsApp client with the phone number.

```php
AdvancedTextEntry::make('phone')
    ->whatsappable()
```

If you want to apply a WhatsApp-able based on a condition, you can pass a closure that returns a boolean value.

```php
AdvancedTextEntry::make('phone')
    ->whatsappable(fn (string $state) => str($state)->startsWith('+')),
```

### Masked

If you want to mask value you can use the **masked** method.

![masked](https://raw.githubusercontent.com/CodeWithDennis/filament-advanced-components-documentation/refs/heads/main/art/masked.png)

```php
AdvancedTextEntry::make('phone')
    ->masked()
```

You can change the mask character by passing a **maskCharacters** option to the component.

```php
AdvancedTextEntry::make('phone')
    ->masked()
    ->maskCharacters('█')
```

If you want to start the mask from a specific index, you can add a **maskIndex** option to the component.

```php
AdvancedTextEntry::make('phone')
    ->masked()
    ->maskIndex(5)
```

The length of the mask can be changed by adding a **maskLength** option to the component. When the length is set to `null` (default), the mask will be applied to the whole value.

```php
AdvancedTextEntry::make('phone')
    ->masked()
    ->maskLength(5)
```

If you want to apply a mask based on a condition, you can pass a closure that returns a boolean value.

```php
AdvancedTextEntry::make('phone')
    ->masked(fn() => ! auth()->user()->is_admin)
```

### Bold

If you want to make the text bold, you can use the **bold** method.

```php
AdvancedTextEntry::make('name')
    ->bold()
```

### Underline

If you want to underline the text, you can use the **underline** method.

```php
AdvancedTextEntry::make('name')
    ->underline()
```

### Italic

If you want to italicize a value, you can use the **italic** method.

```php
AdvancedTextEntry::make('name')
    ->italic()
```

### StrikeThrough

If you want to "strikethrough" a value, you can use the **strikeThrough** method.

```php
AdvancedTextEntry::make('name')
    ->strikeThrough()
```

### Badges

If you want to add badges to a `AdvancedTextEntry`, you can use the **badges** method.

```php
AdvancedTextEntry::make('name')
    ->badges(function(Model $record) {
        return [
            AdvancedBadge::make('quality')
                ->label('Gold'),
        ];
    })
```

#### Border

If you want to have a border on your badge you can use the **border** method.

```php
AdvancedBadge::make('gold')
    ->border()
```

#### Pulse

If you want to make a badge pulse you can use the **pulse** method.

```php
AdvancedBadge::make('gold')
    ->pulse()
```

#### Bounce

If you want to make a badge bounce you can use the **bounce** method.

```php
AdvancedBadge::make('gold')
    ->bounce()
```

#### Border radius

If you want to change the border radius of the badge you can use the **borderRadius** method.

```php
AdvancedBadge::make('quality')
    ->borderRadius(5) // 5px
```

#### Color

If you want to change the color of the badge you can use the **color** method.

```php
AdvancedBadge::make('quality')
    ->color('warning')
```

## AdvancedTextColumn

### Suffix image

You can add an image as a suffix to the text column. The image will be displayed on the right side of the text column.

```php
AdvancedTextColumn::make('country.name')
    ->suffixImage(fn (Country $record) => asset('images/'.$record->image))
    ->suffixImageSize(16)
    ->suffixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

### Prefix image

You can add an image as a prefix to the text column. The image will be displayed on the left side of the text column.

```php
AdvancedTextColumn::make('country.name')
    ->prefixImage(fn (Country $record) => asset('images/'.$record->image))
    ->prefixImageSize(16)
    ->prefixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

### Mailable

You can make the text column mailable. When clicked, it will open the default email client with the state value.

```php
AdvancedTextColumn::make('email')
    ->mailable()
```

If you want to apply a mailable based on a condition, you can pass a closure that returns a boolean value.

```php
AdvancedTextColumn::make('email')
    ->mailable(fn (string $state) => str($state)->endsWith('.com'))
```

### Callable

A simple way to make a value clickable and open the default phone client with the phone number.

```php
AdvancedTextColumn::make('phone')
    ->callable()
```

If you want to apply a callable based on a condition, you can pass a closure that returns a boolean value.

```php
AdvancedTextColumn::make('phone')
    ->callable(fn (string $state) => str($state)->startsWith('+')),
```

### WhatsApp-able

A simple way to make a value clickable and open the default WhatsApp client with the phone number.

```php
AdvancedTextColumn::make('phone')
    ->whatsappable()
```

If you want to apply a WhatsApp-able based on a condition, you can pass a closure that returns a boolean value.

```php
AdvancedTextColumn::make('phone')
    ->whatsappable(fn (string $state) => str($state)->startsWith('+')),
```

### Masked

If you want to mask value you can use the **masked** method.

```php
AdvancedTextColumn::make('phone')
    ->masked()
```

You can change the mask character by passing a **maskCharacters** option to the component.

```php
AdvancedTextColumn::make('phone')
    ->masked()
    ->maskCharacters('█')
```

If you want to start the mask from a specific index, you can add a **maskIndex** option to the component.

```php
AdvancedTextColumn::make('phone')
    ->masked()
    ->maskIndex(5)
```

The length of the mask can be changed by adding a **maskLength** option to the component. When the length is set to `null` (default), the mask will be applied to the whole value.

```php
AdvancedTextColumn::make('phone')
    ->masked()
    ->maskLength(5)
```

If you want to apply a mask based on a condition, you can pass a closure that returns a boolean value.

```php
AdvancedTextColumn::make('phone')
    ->masked(fn() => ! auth()->user()->is_admin)
```

### Bold

If you want to make the text bold, you can use the **bold** method.

```php
AdvancedTextColumn::make('name')
    ->bold()
```

### Underline

If you want to underline the text, you can use the **underline** method.

```php
AdvancedTextColumn::make('name')
    ->underline()
```

### Italic

If you want to italicize a value, you can use the **italic** method.

```php
AdvancedTextColumn::make('name')
    ->italic()
```

### StrikeThrough

If you want to "strikethrough" a value, you can use the **strikeThrough** method.

```php
AdvancedTextColumn::make('name')
    ->strikeThrough()
```

### Badges

If you want to add badges to a `AdvancedTextColumn`, you can use the **badges** method.

![badges](https://raw.githubusercontent.com/CodeWithDennis/filament-advanced-components-documentation/refs/heads/main/art/badges.png)

```php
AdvancedTextColumn::make('name')
    ->badges(function(Model $record) {
        return [
            AdvancedBadge::make('quality')
                ->label('Gold'),
        ];
    })
```

#### Border

If you want to have a border on your badge you can use the **border** method.

```php
AdvancedBadge::make('gold')
    ->border()
```

#### Pulse

If you want to make a badge pulse you can use the **pulse** method.

```php
AdvancedBadge::make('gold')
    ->pulse()
```

#### Bounce

If you want to make a badge bounce you can use the **bounce** method.

```php
AdvancedBadge::make('gold')
    ->bounce()
```

#### Border radius

If you want to change the border radius of the badge you can use the **borderRadius** method.

```php
AdvancedBadge::make('quality')
    ->borderRadius(5) // 5px
```

#### Color

If you want to change the color of the badge you can use the **color** method.

```php
AdvancedBadge::make('quality')
    ->color('warning')
```

## AdvancedTextarea

### Character count

To display the character count, use the `characterCount()` method. If you want live character count, you need to make your field `live`.

```php
AdvancedTextarea::make('description')
    ->characterCount()
```

### Character limit

To show the character limit, use the `characterLimit()` method.

![count-textarea](https://raw.githubusercontent.com/CodeWithDennis/filament-advanced-components-documentation/refs/heads/main/art/count-textarea.png)

> [!WARNING]  
> This is only **visual** and does not enforce the limit.

```php
AdvancedTextarea::make('description')
    ->characterCount()
    ->characterLimit(500),
```

## AdvancedTextInput

### Copyable

To make an advanced text input field copyable, use the `copyable()` method.

```php
AdvancedTextInput::make('email')
    ->copyable(),
```

### Character count

To display the character count, use the `characterCount()` method. If you want live character count, you need to make your field `live`.

![character-count-text-input](https://raw.githubusercontent.com/CodeWithDennis/filament-advanced-components-documentation/refs/heads/main/art/count-text-input.png)

```php
AdvancedTextInput::make('description')
    ->characterCount()
```

### Character limit

To show the character limit, use the `characterLimit()` method.

> [!WARNING]  
> This is only **visual** and does not enforce the limit.

```php
AdvancedTextInput::make('description')
    ->characterCount()
    ->characterLimit(500),
```

### AdvancedToggleButtonsFilter

Similar to the `ToggleButtons` form component, the `AdvancedToggleButtonsFilter` allows you to filter using toggle buttons.

```php
->filters([
    AdvancedToggleButtonsFilter::make('status')
        ->options(CompanyStatus::class)
        ->inline(),
])
```

### AdvancedSelectFilter

Similar to the `AdvancedSelect` form component, the `AdvancedSelectFilter` allows you to filter using a select dropdown.

![advanced-select-filter](https://raw.githubusercontent.com/CodeWithDennis/filament-advanced-components-documentation/refs/heads/main/art/advanced-select-filter.png)

### Suffix image

You can add an image as a suffix to the text column. The image will be displayed on the right side of the text column.

```php
AdvancedSelectFilter::make('country.name')
    ->relationship('country', 'name')
    ->suffixImage(fn (Country $record) => asset('images/'.$record->image))
    ->suffixImageSize(32)
    ->suffixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

### Prefix image

You can add an image as a prefix to the text column. The image will be displayed on the left side of the text column.

```php
AdvancedSelectFilter::make('country.name')
    ->relationship('country', 'name')
    ->prefixImage(fn (Country $record) => asset('images/'.$record->image))
    ->prefixImageSize(32)
    ->prefixImageExtraAttributes([
        'class' => 'pr-4',
    ]),
```

## Code Distribution

Licenses strictly prohibit the public distribution of its source code. This means you are not permitted to use Filament Advanced Components to build an application and then distribute that application publicly through open-source repositories, hosting platforms, or any other code-sharing platforms.