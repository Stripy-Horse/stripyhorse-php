# StripyHorse\RenderApi



All URIs are relative to https://api.stripyhorse.io, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**preflightLabel()**](RenderApi.md#preflightLabel) | **POST** /v1/preflight | Grade a label&#39;s barcodes before they ship |
| [**renderZpl()**](RenderApi.md#renderZpl) | **POST** /v1/render | Render ZPL to PNG images |
| [**renderZplPng()**](RenderApi.md#renderZplPng) | **POST** /v1/render.png | Render ZPL and return the first label as a raw PNG |


## `preflightLabel()`

```php
preflightLabel($preflight_input_body): \StripyHorse\Model\PreflightOutputBody
```

Grade a label's barcodes before they ship

Renders the ZPL and grades every barcode the way a verifier grades a printed label: round-trip decode, measured module width in printer dots, dot-grid alignment (catches rasterized barcodes), quiet zones in modules, physical X-dimension against the spec minimum, blur tolerance, and a cross-density table - plus static lint findings (structure, encoding traps, out-of-bounds fields). Grade fail means a scanner will reject it; fix it before a truck does.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: headerKey
$config = StripyHorse\Configuration::getDefaultConfiguration()->setApiKey('X-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = StripyHorse\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Api-Key', 'Bearer');

// Configure Bearer (sh_live_…) authorization: bearerKey
$config = StripyHorse\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new StripyHorse\Api\RenderApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$preflight_input_body = new \StripyHorse\Model\PreflightInputBody(); // \StripyHorse\Model\PreflightInputBody

try {
    $result = $apiInstance->preflightLabel($preflight_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RenderApi->preflightLabel: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **preflight_input_body** | [**\StripyHorse\Model\PreflightInputBody**](../Model/PreflightInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\PreflightOutputBody**](../Model/PreflightOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `renderZpl()`

```php
renderZpl($render_input_body): \StripyHorse\Model\RenderOutputBody
```

Render ZPL to PNG images

Renders every label in the ZPL stream. For a raw PNG of a single label use renderZplPng.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: headerKey
$config = StripyHorse\Configuration::getDefaultConfiguration()->setApiKey('X-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = StripyHorse\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Api-Key', 'Bearer');

// Configure Bearer (sh_live_…) authorization: bearerKey
$config = StripyHorse\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new StripyHorse\Api\RenderApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$render_input_body = new \StripyHorse\Model\RenderInputBody(); // \StripyHorse\Model\RenderInputBody

try {
    $result = $apiInstance->renderZpl($render_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RenderApi->renderZpl: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **render_input_body** | [**\StripyHorse\Model\RenderInputBody**](../Model/RenderInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\RenderOutputBody**](../Model/RenderOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `renderZplPng()`

```php
renderZplPng($render_input_body): string
```

Render ZPL and return the first label as a raw PNG

curl-friendly variant: the X-Label-Count response header carries the total label count.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: headerKey
$config = StripyHorse\Configuration::getDefaultConfiguration()->setApiKey('X-Api-Key', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = StripyHorse\Configuration::getDefaultConfiguration()->setApiKeyPrefix('X-Api-Key', 'Bearer');

// Configure Bearer (sh_live_…) authorization: bearerKey
$config = StripyHorse\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new StripyHorse\Api\RenderApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$render_input_body = new \StripyHorse\Model\RenderInputBody(); // \StripyHorse\Model\RenderInputBody

try {
    $result = $apiInstance->renderZplPng($render_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling RenderApi->renderZplPng: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **render_input_body** | [**\StripyHorse\Model\RenderInputBody**](../Model/RenderInputBody.md)|  | |

### Return type

**string**

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
