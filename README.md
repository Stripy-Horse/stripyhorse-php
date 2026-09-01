# Stripy Horse PHP SDK

Official PHP client for the [Stripy Horse](https://stripyhorse.io) API - Zebra/ZPL
developer tools: render ZPL to PNG, convert PDFs/images/HTML to print-ready ZPL,
and drive hosted virtual Zebra printers from your tests.

Generated from the live [OpenAPI spec](https://stripyhorse.io/openapi.yaml), which is
itself emitted from the server's handler code, so the SDK can never drift from the API.

Requires PHP 8.1+.

## Install

```bash
composer require stripyhorse/stripyhorse-php
```

## Setup

```php
require_once 'vendor/autoload.php';

$config = StripyHorse\Configuration::getDefaultConfiguration()
    ->setAccessToken('sh_live_YOUR_KEY');
```

## Render ZPL to PNG

```php
$render = new StripyHorse\Api\RenderApi(null, $config);
$out = $render->renderZpl(new StripyHorse\Model\RenderInputBody([
    'zpl'    => '^XA^FO50,50^A0N,45,45^FDHello^FS^XZ',
    'preset' => '4x6',
]));
file_put_contents('label.png', base64_decode($out->getLabels()[0]->getPng()));
```

## Convert a PDF (or PNG/GIF/JPEG) to ZPL

```php
$convert = new StripyHorse\Api\ConvertApi(null, $config);
$result = $convert->convertDocument(new SplFileObject('shipping-label.pdf'), preset: '4x6');
foreach ($result->getPages() as $page) {
    // send $page->getZpl() to your printer
}
```

## Design a label in HTML, get ZPL

```php
$out = $convert->convertHtml(new StripyHorse\Model\HtmlInputBody([
    'html'   => '<div style="position:absolute;left:40px;top:40px;font-size:50px">Hello</div>
                 <zpl-barcode type="code128" data="00123456789"
                   style="left:40px;top:150px;width:600px;height:150px"></zpl-barcode>',
    'preset' => '4x6',
]));
echo $out->getZpl();
```

## Test label printing in CI with a virtual printer

```php
$sim = new StripyHorse\Api\SimulatorApi(null, $config);

$printer = $sim->createPrinter(new StripyHorse\Model\CreatePrinterInputBody([
    'name' => 'ci-run-42', 'preset' => '4x6',
]));

// Point the system under test at the printer, exactly like hardware:
$addr = $printer->getTcp()->getHost() . ':' . $printer->getTcp()->getPort();

// ... run your fulfillment code against $addr ...

// Then assert on what it printed:
$jobs = $sim->listJobs($printer->getId());
assert(count($jobs->getJobs()) === 1);

// Reproduce a paper-out jam and watch jobs hold in the buffer:
$sim->setPrinterFaults($printer->getId(), new StripyHorse\Model\Faults(['paper_out' => true]));
```

## Errors

API errors throw `StripyHorse\ApiException`; `$e->getResponseBody()` carries the
JSON error envelope. HTTP 429 includes a `Retry-After` header.

## Regenerating

Every file here is generated from the [OpenAPI spec](https://stripyhorse.io/openapi.yaml),
which is emitted from the server's own handler code. Hand edits are overwritten by the
next spec change, so report a problem with the SDK as a problem with the API:
[stripyhorse.io/contact](https://stripyhorse.io/contact).
