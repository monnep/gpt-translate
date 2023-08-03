# GPT-Translate for Laravel

`gpt-translate` is a package for Laravel that allows you to generate a translation file based on translation strings found throughout your application. You can call these strings using `__()`, `@lang()`, `$t()`, or `trans()`, and they can be located in php, js, ts, or vue files.

Furthermore, `gpt-translate` enables you to translate your base language file, whether you previously had it or generated it using the package, to other languages using the ChatGPT API. Supported languages for translation include English, Spanish, French, German, Italian, and Portuguese.

## Getting Started

**Installation**  
   Install the package using composer:
```bash
composer require rdosgroup/gpt-translate
```

**Add Service Provider**
Add the following to your `config/app.php` file:
```php
'providers' => [
    ...
    Rdosgroup\GptTranslate\GptTranslateServiceProvider::class,
    ...
],
```


**Publish the Configuration File**  
You need to publish the `openai.php` configuration file:
```bash
php artisan vendor:publish
```


**Environment Configuration**  
Add the `OPENAI_API_KEY` and `OPENAI_ORGANIZATION` variables to your `.env` file with the details from your OpenAI account.

**Generate Base Translation File**  
If you don’t already have a base translation file, generate it using:
```bash
php artisan translate:make --lang=en
```
As shown, this command creates a `lang/en.json` in your root folder. If your application is in another language, pass the appropriate `lang` parameter, e.g., for French:
```bash
php artisan translate:make --lang=fr
```


**Translate with ChatGPT**  
After having your base translation file, whether generated by the package or otherwise, run the translation command for ChatGPT to do the translation, e.g.:
```bash
php artisan translate:lang --origin=en --lang=fr
```
This translates the original `en.json` to French and creates a new `fr.json` file.

**Provide Context (Optional)**  
For more accurate translations, briefly describe the context of your application’s purpose. This helps ChatGPT better understand and translate the text. Use the `context` parameter:
```bash
php artisan translate:lang --origin=en --lang=fr --context="a pet product sales application"
```


**Specify the Model (Optional)**  
By default, the package uses GPT-3.5. If desired, specify any other OpenAI model compatible with the Chat API:
```bash
php artisan translate:lang --origin=en --lang=fr --model=gpt-4
```


## Conclusion

Leverage the power of ChatGPT and the flexibility of `gpt-translate` to localize your Laravel application effectively and efficiently.
