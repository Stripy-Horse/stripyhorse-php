# StripyHorse\ConvertApi



All URIs are relative to https://api.stripyhorse.io, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**convertBatch()**](ConvertApi.md#convertBatch) | **POST** /v1/convert/batch | Convert many documents in one request, results streamed |
| [**convertDocument()**](ConvertApi.md#convertDocument) | **POST** /v1/convert | Convert a PDF or image to ZPL |
| [**convertHtml()**](ConvertApi.md#convertHtml) | **POST** /v1/convert/html | Convert an HTML label design to ZPL |
| [**convertZplToHtml()**](ConvertApi.md#convertZplToHtml) | **POST** /v1/convert/zpl-html | Decompile ZPL into editable HTML |


## `convertBatch()`

```php
convertBatch($files, $barcode_aware, $compression, $dpmm, $height_mm, $preset, $rotation, $scale, $threshold, $width_mm)
```

Convert many documents in one request, results streamed

Upload up to 20 PDFs/images as repeated `files` fields. The response is application/x-ndjson: one JSON object per converted page, streamed as each page finishes — `{\"file\":…,\"page\":…,\"pageCount\":…,\"zpl\":…}` on success, `{\"file\":…,\"error\":…}` per failed file (remaining files still convert).

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


$apiInstance = new StripyHorse\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$files = array('/path/to/file.txt'); // \SplFileObject[]
$barcode_aware = True; // bool
$compression = 'compression_example'; // string
$dpmm = 56; // int
$height_mm = 3.4; // float
$preset = 'preset_example'; // string
$rotation = 56; // int
$scale = 'scale_example'; // string
$threshold = 56; // int
$width_mm = 3.4; // float

try {
    $apiInstance->convertBatch($files, $barcode_aware, $compression, $dpmm, $height_mm, $preset, $rotation, $scale, $threshold, $width_mm);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->convertBatch: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **files** | **\SplFileObject[]**|  | |
| **barcode_aware** | **bool**|  | [optional] |
| **compression** | **string**|  | [optional] |
| **dpmm** | **int**|  | [optional] |
| **height_mm** | **float**|  | [optional] |
| **preset** | **string**|  | [optional] |
| **rotation** | **int**|  | [optional] |
| **scale** | **string**|  | [optional] |
| **threshold** | **int**|  | [optional] |
| **width_mm** | **float**|  | [optional] |

### Return type

void (empty response body)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `convertDocument()`

```php
convertDocument($file, $barcode_aware, $compression, $dpmm, $height_mm, $preset, $rotation, $scale, $threshold, $width_mm): \StripyHorse\Model\ConvertOutputBody
```

Convert a PDF or image to ZPL

Each page becomes its own ^GFA command (Zebra ACS run-length compression). PDFs up to 16 pages.

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


$apiInstance = new StripyHorse\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$file = '/path/to/file.txt'; // \SplFileObject | PDF, PNG, GIF or JPEG
$barcode_aware = True; // bool | EXPERIMENTAL: re-emit decodable barcodes as native ^BC/^BQ fields, verified by a decode round trip with automatic fallback to plain rasterization
$compression = 'compression_example'; // string | acs (default) or z64 (zlib+base64, smaller payloads)
$dpmm = 56; // int
$height_mm = 3.4; // float
$preset = 'preset_example'; // string
$rotation = 56; // int
$scale = 'scale_example'; // string | cover (fit), fill (stretch) or none
$threshold = 56; // int
$width_mm = 3.4; // float

try {
    $result = $apiInstance->convertDocument($file, $barcode_aware, $compression, $dpmm, $height_mm, $preset, $rotation, $scale, $threshold, $width_mm);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->convertDocument: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **file** | **\SplFileObject****\SplFileObject**| PDF, PNG, GIF or JPEG | |
| **barcode_aware** | **bool**| EXPERIMENTAL: re-emit decodable barcodes as native ^BC/^BQ fields, verified by a decode round trip with automatic fallback to plain rasterization | [optional] |
| **compression** | **string**| acs (default) or z64 (zlib+base64, smaller payloads) | [optional] |
| **dpmm** | **int**|  | [optional] |
| **height_mm** | **float**|  | [optional] |
| **preset** | **string**|  | [optional] |
| **rotation** | **int**|  | [optional] |
| **scale** | **string**| cover (fit), fill (stretch) or none | [optional] |
| **threshold** | **int**|  | [optional] |
| **width_mm** | **float**|  | [optional] |

### Return type

[**\StripyHorse\Model\ConvertOutputBody**](../Model/ConvertOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `convertHtml()`

```php
convertHtml($html_input_body): \StripyHorse\Model\HtmlOutputBody
```

Convert an HTML label design to ZPL

Renders the HTML at exact print resolution (headless Chrome, network access blocked) and rasterizes it — except `<zpl-barcode type=\"code128|qr\" data=\"…\">` elements, which are measured from the layout and emitted as native ^BC/^BQ fields at their exact boxes. Size and position them with CSS (`left/top/width/height`); optional `module` (^BY dots) and `mag` (QR magnification) attributes pin exact bar geometry instead of fitting it to the box. Unsupported types or unencodable data fail loudly.  **PHP** (`composer require stripyhorse/stripyhorse-php`): ```php $out = $convert->convertHtml(new StripyHorse\\Model\\HtmlInputBody([     'html' => '<div style=\"position:absolute;left:40px;top:40px;font-size:50px\">Hello</div>',     'preset' => '4x6', ])); echo $out->getZpl(); ```

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


$apiInstance = new StripyHorse\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$html_input_body = new \StripyHorse\Model\HtmlInputBody(); // \StripyHorse\Model\HtmlInputBody

try {
    $result = $apiInstance->convertHtml($html_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->convertHtml: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **html_input_body** | [**\StripyHorse\Model\HtmlInputBody**](../Model/HtmlInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\HtmlOutputBody**](../Model/HtmlOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `convertZplToHtml()`

```php
convertZplToHtml($zpl_html_input_body): \StripyHorse\Model\ZplHTMLOutputBody
```

Decompile ZPL into editable HTML

The migration path for legacy ZPL templates: text, boxes and Code128/QR barcodes become editable HTML in the dialect convertHtml accepts; unsupported elements (raster graphics, exotic barcodes) are embedded as positioned images so the layout survives. Round-tripping through convertHtml preserves scannable barcodes.

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


$apiInstance = new StripyHorse\Api\ConvertApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$zpl_html_input_body = new \StripyHorse\Model\ZplHTMLInputBody(); // \StripyHorse\Model\ZplHTMLInputBody

try {
    $result = $apiInstance->convertZplToHtml($zpl_html_input_body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ConvertApi->convertZplToHtml: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **zpl_html_input_body** | [**\StripyHorse\Model\ZplHTMLInputBody**](../Model/ZplHTMLInputBody.md)|  | |

### Return type

[**\StripyHorse\Model\ZplHTMLOutputBody**](../Model/ZplHTMLOutputBody.md)

### Authorization

[headerKey](../../README.md#headerKey), [bearerKey](../../README.md#bearerKey)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
