# Barcode

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**blur_margin_dots** | **int** | Largest blur radius the symbol survives; 0 &#x3D; no margin |
**checks** | [**\StripyHorse\Model\Check[]**](Check.md) |  |
**cross_dpi** | [**\StripyHorse\Model\DPIVerdict[]**](DPIVerdict.md) | X-dimension at other print densities, same dot counts | [optional]
**format** | **string** | CODE_128, CODE_39, ITF, QR_CODE, DATA_MATRIX |
**module_dots** | **float** | Measured narrow-element width in printer dots (1D only) | [optional]
**quiet_left_modules** | **float** |  | [optional]
**quiet_right_modules** | **float** |  | [optional]
**value** | **string** |  |
**x_dimension_mm** | **float** | Physical narrow-element width at the analyzed density | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
