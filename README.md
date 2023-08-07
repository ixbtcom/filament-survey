# Filament Laravel Survey

A Filament plugin for [Laravel Survey](https://github.com/matt-daneshvar/laravel-survey) package.

This package provides Filament resources for [Laravel Survey](https://github.com/matt-daneshvar/laravel-survey).

## Requirements
- PHP 8.1
- [Filament 3](https://github.com/laravel-filament/filament)

## Dependencies
- [maatwebsite/excel](https://github.com/SpartnerNL/Laravel-Excel)
- [matt-daneshvar/laravel-survey](https://github.com/matt-daneshvar/laravel-survey)
- [spatie/eloquent-sortable](https://github.com/spatie/eloquent-sortable)

## Installation

This plugin uses [Spatie translatable](https://spatie.be/docs/laravel-translatable/v6/installation-setup), [Spatie translatable plugin](https://filamentphp.com/plugins/filament-spatie-translatable), and [Laravel Excel](https://github.com/SpartnerNL/Laravel-Excel), and [Eloquent Sortable](https://github.com/spatie/eloquent-sortable) packages.

First install and configure these packages, then proceed to the plugin installation instructions below.

> **Note** 
> It also uses a modifed version of [Laravel Survey](https://github.com/matt-daneshvar/laravel-survey):
> https://github.com/tappnetwork/laravel-survey/tree/translatable that adds translatable and sortable fields to the survey models.
> More details in this PR: https://github.com/matt-daneshvar/laravel-survey/pull/39


You can install the plugin via Composer:

```bash
composer require tapp/filament-survey:"^3.0"
```

> **Note** 
> For **Filament 2.x** check the **[2.x](https://github.com//TappNetwork/filament-survey/tree/2.x)** branch

Publish the migrations with:

```bash
php artisan vendor:publish --tag="filament-survey-migrations"
```

Run migrations:

```bash
php artisan migrate
```


You can publish the view file with:

```bash
php artisan vendor:publish --tag="filament-survey-views"
```

You can publish the translations files with:

```bash
php artisan vendor:publish --tag="filament-survey-translations"
```

You can publish the config file with:

```bash
php artisan vendor:publish --tag="filament-survey-config"
```

This is the content of the published config file:

```php
<?php

return [

    'resources' => [
        'AnswerResource' => \Tapp\FilamentSurvey\Resources\AnswerResource::class,
        'EntryResource' => \Tapp\FilamentSurvey\Resources\EntryResource::class,
        'QuestionResource' => \Tapp\FilamentSurvey\Resources\QuestionResource::class,
        'SectionResource' => \Tapp\FilamentSurvey\Resources\SectionResource::class,
        'SurveyResource' => \Tapp\FilamentSurvey\Resources\SurveyResource::class,
    ],

    'languages' => [
        'en' => 'English',
        'es' => 'Spanish',
    ],

    'navigation' => [
        'answer' => [
            'sort' => 4,
            'icon' => 'heroicon-o-reply',
        ],
        'entry' => [
            'sort' => 5,
            'icon' => 'heroicon-o-view-list',
        ],
        'question' => [
            'sort' => 3,
            'icon' => 'heroicon-o-question-mark-circle',
        ],
        'section' => [
            'sort' => 2,
            'icon' => 'heroicon-o-folder-open',
        ],
        'survey' => [
            'sort' => 1,
            'icon' => 'heroicon-o-collection',
        ],
    ],

];
```

## Adding the plugin to a panel

Add this plugin to a panel on `plugins()`method. E.g. in  `app/Providers/Filament/AdminPanelProvider.php`:

```php
use Tapp\FilamentSurvey\FilamentSurveyPlugin;
 
public function panel(Panel $panel): Panel
{
    return $panel
        // ...
        ->plugins([
            FilamentSurveyPlugin::make(),
            //...
        ]);
}
```

This plugin requires the Spatie Translatable plugin, so it should also be added on a panel like so:

```php
use Filament\SpatieLaravelTranslatablePlugin;
use Tapp\FilamentSurvey\FilamentSurveyPlugin;
 
public function panel(Panel $panel): Panel
{
    return $panel
        // ...
        ->plugins([
            FilamentSurveyPlugin::make(),
            SpatieLaravelTranslatablePlugin::make(),
            //...
        ]);
}
```
