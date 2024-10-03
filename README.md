# yzhanJSONTranslater

JSON language translater using OpenAI with cache. 使用 AI 将 JSON 翻译成不同语言，缓存结果以节省费用

## Features

- **JSON Translation**: Translates the values of a JSON object into multiple languages while keeping the keys unchanged.
- **OpenAI Integration**: Uses the OpenAI API to provide accurate and high-quality translations.
- **Caching**: Caches the results to optimize API usage and save costs.
- **Customizable**: Allows configuring the API client and endpoints.

## Installation

1. Install the library via Composer:

```bash
composer require mantoufan/yzhanjsontranslater
```

2. Install development dependencies for testing purposes:

```bash
composer install --dev
```

## Usage

Here's an example of how to use the YZhanJSONTranslater to translate JSON objects:

```php
use YZhanJSONTranslater\YZhanJSONTranslater;

$translator = new YZhanJSONTranslater(array(
  'client' => 'OpenAI',
  'apiKey' => 'your-openai-api-key',
  'organization' => 'your-openai-organization',
  'apiUrl' => 'https://api.openai.com',
));

$json = array('hello' => 'hello');
$translatedJson = $translator->translate($json, 'zh-CN'); // Translates to Simplified Chinese
print_r($translatedJson);
```

## Environment Variables

The library relies on the following environment variables to configure OpenAI:

- `OPENAI_APIKEY`: Your OpenAI API key.
- `OPENAI_APIURL`: The OpenAI API base URL (default: `https://api.openai.com`).
- `OPENAI_ORGANIZATION`: Your OpenAI organization ID.

Use a `.env` file to provide these environment variables:

```
OPENAI_APIKEY=your-openai-api-key
OPENAI_APIURL=https://api.openai.com
OPENAI_ORGANIZATION=your-openai-organization
```

## Testing

The library uses PHPUnit for testing. You can run the tests using:

```bash
composer test
```

To generate a test coverage report:

```bash
composer coverage
```

## Example Test Case

The `YZhanJSONTranslaterTest` includes unit tests to ensure the correctness of the translation functionality.

```php
public function dataProvider(): array {
  return array(
    array(array('hello' => 'hello'), 'zh-CN', array('hello' => '你好')),
    array(array('hello' => 'hello'), 'zh-TW', array('hello' => '你好')),
    array(array('hello' => 'hello'), 'jp', array('hello' => 'こんにちは')),
    array(array('hello' => '你好'), 'en', array('hello' => 'hello')),
  );
}
```

## Requirements

- PHP >= 5.4
- OpenAI API key
- Composer

## License

This project is licensed under the MIT License. See the [LICENSE](https://opensource.org/licenses/MIT) file for details.

## Contribution

Feel free to contribute by submitting issues or pull requests.
