# StripyHorse\PrintersApi



All URIs are relative to https://api.stripyhorse.io, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**parseHostStatus()**](PrintersApi.md#parseHostStatus) | **POST** /v1/host-status/parse | Decode a Zebra ~HS host status response |


## `parseHostStatus()`

```php
parseHostStatus($host_status_input_body): \StripyHorse\Model\HostStatusOutputBody
```

Decode a Zebra ~HS host status response

Parses the three-line ~HS answer a Zebra printer (or our virtual printer) returns on port 9100 into typed fields - paper out, pause, buffer contents, head temperature - so you never write a positional comma parser. Accepts raw bytes, cat -v style ^B/^C markers, or hand-cleaned lines. Does not count against your monthly quota.

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


$apiInstance = new StripyHorse\Api\PrintersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$host_status_input_body = new \StripyHorse\Model\HostStatusInputBody(); // \StripyHorse\Model\HostStatusInputBody

try {
    $result = $apiInstance->parseHostStatus($host_status_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PrintersApi->parseHostStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **host_status_input_body** | [**\StripyHorse\Model\HostStatusInputBody**](../Model/HostStatusInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\HostStatusOutputBody**](../Model/HostStatusOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
