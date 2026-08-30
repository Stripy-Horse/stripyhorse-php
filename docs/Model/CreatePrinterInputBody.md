# CreatePrinterInputBody

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**access_mode** | **string** | Who may print to the TCP port; default open. Use token from CI, where the source address is different every run. | [optional]
**anonymize** | **bool** | Mask PII and strip graphics from every captured frame | [optional]
**dpmm** | **int** | Print density in dots/mm (152/203/300/600 dpi); default 8 | [optional]
**height_mm** | **float** |  | [optional]
**mode** | **string** |  | [optional]
**name** | **string** |  |
**preset** | **string** | Named label size in inches; alternative to widthMm/heightMm | [optional]
**webhook_url** | **string** |  | [optional]
**width_mm** | **float** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
