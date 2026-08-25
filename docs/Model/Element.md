# Element

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**align** | **string** | Alignment when wrapping | [optional]
**corner_radius** | **int** | Box corner rounding 0-8 | [optional]
**data** | **string** | Barcode payload; {{name}} interpolates | [optional]
**diameter** | **int** | Circle diameter in dots | [optional]
**error_correction** | **string** | QR error correction (default M) | [optional]
**font** | **string** | Printer font: 0 (scalable, default) or A-Z | [optional]
**font_height** | **int** | Character height in dots (text) | [optional]
**font_width** | **int** | Character width in dots; 0 follows fontHeight | [optional]
**height** | **int** | Bar height in dots (1D) / box height in dots (box) | [optional]
**length** | **int** | Line length in dots | [optional]
**lines** | **int** | Max lines when wrapping (default 1) | [optional]
**magnification** | **int** | QR module magnification (default 3) | [optional]
**max_width** | **int** | Wrap text into a block this many dots wide | [optional]
**module_size** | **int** | DataMatrix module size in dots (default 4) | [optional]
**module_width** | **int** | Narrow element width in dots (1D; default 3) | [optional]
**orientation** | **string** | Line direction | [optional]
**png** | **string** | PNG/GIF/JPEG, base64-encoded | [optional]
**print_text** | **bool** | Print the human-readable line under 1D barcodes (default true) | [optional]
**rotation** | **int** |  | [optional]
**text** | **string** | Text content; {{name}} interpolates from variables | [optional]
**thickness** | **int** | Stroke thickness in dots (default 1) | [optional]
**threshold** | **int** | Bitonal threshold (default 128) | [optional]
**type** | **string** | What to place |
**width** | **int** | Box/image width in dots | [optional]
**x** | **int** | Left edge in dots | [optional]
**y** | **int** | Top edge in dots | [optional]
**zpl** | **string** | Verbatim ZPL commands (raw only) - the escape hatch | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
