# StripyHorse\ComposeApi



All URIs are relative to https://api.stripyhorse.io, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**composeLabel()**](ComposeApi.md#composeLabel) | **POST** /v1/labels/compose | Compose ZPL from typed JSON elements |


## `composeLabel()`

```php
composeLabel($compose_input_body): \StripyHorse\Model\ComposeOutputBody
```

Compose ZPL from typed JSON elements

Labels as JSON: place text, barcodes (code128/39, QR, DataMatrix), boxes, lines, circles, images and raw ZPL passthrough on a label and get back ZPL - optionally with rendered previews. {{name}} in text/data interpolates from the variables map; an unresolved variable is an error, never a blank on a real shipment. Positions are printer dots.

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


$apiInstance = new StripyHorse\Api\ComposeApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$compose_input_body = new \StripyHorse\Model\ComposeInputBody(); // \StripyHorse\Model\ComposeInputBody

try {
    $result = $apiInstance->composeLabel($compose_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ComposeApi->composeLabel: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **compose_input_body** | [**\StripyHorse\Model\ComposeInputBody**](../Model/ComposeInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\ComposeOutputBody**](../Model/ComposeOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
