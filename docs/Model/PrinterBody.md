# PrinterBody

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**anonymize** | **bool** | When true, PII is masked and graphics stripped from every captured frame |
**created_at** | **\DateTime** |  |
**dpmm** | **int** |  |
**expires_at** | **\DateTime** |  | [optional]
**height_mm** | **float** |  |
**id** | **string** |  |
**ingest_url** | **string** | HTTPS print capability URL. Only returned on creation. | [optional]
**mode** | **string** |  |
**name** | **string** |  |
**state** | [**\StripyHorse\Model\StatusSnapshot**](StatusSnapshot.md) |  | [optional]
**tcp** | [**\StripyHorse\Model\PrinterBodyTCPStruct**](PrinterBodyTCPStruct.md) |  |
**webhook_secret** | **string** | HMAC-SHA256 key for X-Stripy-Horse-Signature. Only returned on creation. | [optional]
**webhook_url** | **string** |  | [optional]
**width_mm** | **float** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
