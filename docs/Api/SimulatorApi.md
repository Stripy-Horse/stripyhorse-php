# StripyHorse\SimulatorApi



All URIs are relative to https://api.stripyhorse.io, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**clearJobs()**](SimulatorApi.md#clearJobs) | **DELETE** /v1/printers/{printerId}/jobs | Delete all captured jobs |
| [**createPrinter()**](SimulatorApi.md#createPrinter) | **POST** /v1/printers | Create a virtual printer |
| [**deleteJob()**](SimulatorApi.md#deleteJob) | **DELETE** /v1/printers/{printerId}/jobs/{jobId} | Delete one captured job |
| [**deletePrinter()**](SimulatorApi.md#deletePrinter) | **DELETE** /v1/printers/{printerId} | Delete a printer and its captured jobs |
| [**getJob()**](SimulatorApi.md#getJob) | **GET** /v1/printers/{printerId}/jobs/{jobId} | Get one job including its raw ZPL |
| [**getJobLabel()**](SimulatorApi.md#getJobLabel) | **GET** /v1/printers/{printerId}/jobs/{jobId}/labels/{index}.png | Get one rendered label as a PNG |
| [**getPrinter()**](SimulatorApi.md#getPrinter) | **GET** /v1/printers/{printerId} | Get a printer with live state |
| [**listJobs()**](SimulatorApi.md#listJobs) | **GET** /v1/printers/{printerId}/jobs | List captured jobs, newest first |
| [**listPrinters()**](SimulatorApi.md#listPrinters) | **GET** /v1/printers | List your printers |
| [**loadPrinterMedia()**](SimulatorApi.md#loadPrinterMedia) | **POST** /v1/printers/{printerId}/media | Fit a fresh roll and ribbon |
| [**resetPrinter()**](SimulatorApi.md#resetPrinter) | **POST** /v1/printers/{printerId}/reset | Clear all faults and flush held jobs |
| [**setPrinterFaults()**](SimulatorApi.md#setPrinterFaults) | **POST** /v1/printers/{printerId}/faults | Inject or clear fault conditions |
| [**updatePrinter()**](SimulatorApi.md#updatePrinter) | **PATCH** /v1/printers/{printerId} | Rename a printer or set its webhook URL |


## `clearJobs()`

```php
clearJobs($printer_id)
```

Delete all captured jobs

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string

try {
    $apiInstance->clearJobs($printer_id);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->clearJobs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createPrinter()`

```php
createPrinter($create_printer_input_body): \StripyHorse\Model\PrinterBody
```

Create a virtual printer

Free tier: one ephemeral printer, expiring after 4h with no jobs. Paid tiers: persistent printers. The ingest URL and webhook secret are only returned here.

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_printer_input_body = new \StripyHorse\Model\CreatePrinterInputBody(); // \StripyHorse\Model\CreatePrinterInputBody

try {
    $result = $apiInstance->createPrinter($create_printer_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->createPrinter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_printer_input_body** | [**\StripyHorse\Model\CreatePrinterInputBody**](../Model/CreatePrinterInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\PrinterBody**](../Model/PrinterBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteJob()`

```php
deleteJob($printer_id, $job_id)
```

Delete one captured job

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string
$job_id = 56; // int

try {
    $apiInstance->deleteJob($printer_id, $job_id);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->deleteJob: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |
| **job_id** | **int**|  | |

### Return type

void (empty response body)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deletePrinter()`

```php
deletePrinter($printer_id)
```

Delete a printer and its captured jobs

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string

try {
    $apiInstance->deletePrinter($printer_id);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->deletePrinter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getJob()`

```php
getJob($printer_id, $job_id): \StripyHorse\Model\JobOutputBody
```

Get one job including its raw ZPL

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string
$job_id = 56; // int

try {
    $result = $apiInstance->getJob($printer_id, $job_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->getJob: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |
| **job_id** | **int**|  | |

### Return type

[**\StripyHorse\Model\JobOutputBody**](../Model/JobOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getJobLabel()`

```php
getJobLabel($printer_id, $job_id, $index): string
```

Get one rendered label as a PNG

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string
$job_id = 56; // int
$index = 56; // int

try {
    $result = $apiInstance->getJobLabel($printer_id, $job_id, $index);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->getJobLabel: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |
| **job_id** | **int**|  | |
| **index** | **int**|  | |

### Return type

**string**

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getPrinter()`

```php
getPrinter($printer_id): \StripyHorse\Model\PrinterBody
```

Get a printer with live state

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string

try {
    $result = $apiInstance->getPrinter($printer_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->getPrinter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |

### Return type

[**\StripyHorse\Model\PrinterBody**](../Model/PrinterBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listJobs()`

```php
listJobs($printer_id, $limit, $before): \StripyHorse\Model\ListJobsOutputBody
```

List captured jobs, newest first

For CI assertions and inbox views. Cursor-paged via before.

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string
$limit = 50; // int
$before = 56; // int | Return jobs with id lower than this cursor

try {
    $result = $apiInstance->listJobs($printer_id, $limit, $before);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->listJobs: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |
| **limit** | **int**|  | [optional] [default to 50] |
| **before** | **int**| Return jobs with id lower than this cursor | [optional] |

### Return type

[**\StripyHorse\Model\ListJobsOutputBody**](../Model/ListJobsOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listPrinters()`

```php
listPrinters(): \StripyHorse\Model\ListPrintersOutputBody
```

List your printers

Every printer on your account, whichever of its keys created them.

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listPrinters();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->listPrinters: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\StripyHorse\Model\ListPrintersOutputBody**](../Model/ListPrintersOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `loadPrinterMedia()`

```php
loadPrinterMedia($printer_id, $media_input_body): \StripyHorse\Model\StateOutputBody
```

Fit a fresh roll and ribbon

A loaded roll runs down as labels print and raises paper out when it is spent, which holds everything sent after it. Zero is an endless roll, which is the default and never runs out.

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string
$media_input_body = new \StripyHorse\Model\MediaInputBody(); // \StripyHorse\Model\MediaInputBody

try {
    $result = $apiInstance->loadPrinterMedia($printer_id, $media_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->loadPrinterMedia: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |
| **media_input_body** | [**\StripyHorse\Model\MediaInputBody**](../Model/MediaInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\StateOutputBody**](../Model/StateOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `resetPrinter()`

```php
resetPrinter($printer_id): \StripyHorse\Model\StateOutputBody
```

Clear all faults and flush held jobs

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string

try {
    $result = $apiInstance->resetPrinter($printer_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->resetPrinter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |

### Return type

[**\StripyHorse\Model\StateOutputBody**](../Model/StateOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `setPrinterFaults()`

```php
setPrinterFaults($printer_id, $faults): \StripyHorse\Model\StateOutputBody
```

Inject or clear fault conditions

Blocking faults hold incoming jobs in the receive buffer; clearing them flushes the queue in order.

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string
$faults = new \StripyHorse\Model\Faults(); // \StripyHorse\Model\Faults

try {
    $result = $apiInstance->setPrinterFaults($printer_id, $faults);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->setPrinterFaults: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |
| **faults** | [**\StripyHorse\Model\Faults**](../Model/Faults.md)|  | |

### Return type

[**\StripyHorse\Model\StateOutputBody**](../Model/StateOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updatePrinter()`

```php
updatePrinter($printer_id, $update_printer_input_body): \StripyHorse\Model\PrinterBody
```

Rename a printer or set its webhook URL

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


$apiInstance = new StripyHorse\Api\SimulatorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$printer_id = 'printer_id_example'; // string
$update_printer_input_body = new \StripyHorse\Model\UpdatePrinterInputBody(); // \StripyHorse\Model\UpdatePrinterInputBody

try {
    $result = $apiInstance->updatePrinter($printer_id, $update_printer_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SimulatorApi->updatePrinter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **printer_id** | **string**|  | |
| **update_printer_input_body** | [**\StripyHorse\Model\UpdatePrinterInputBody**](../Model/UpdatePrinterInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\PrinterBody**](../Model/PrinterBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
