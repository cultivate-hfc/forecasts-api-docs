## Bulk External Prediction Sets Creation

In addition to the [External Prediction Set Creation API](/#external-prediction-sets-creation), where you create a single External Prediction Set per request, we also provide a bulk External Prediction Set creation endpoint. This allows you to submit forecasts for many/all active questions for a forecasting method (aka. an External Predictor) in a single request. Each request can only contain forecasts for a single forecasting method. If you need to submit forecasts for 100 forecasting methods, you will need to make 100 requests -- one request per forecasting method.

**Note: all requirements regarding the structure of `external_predictions_attributes` and definition of `external_predictor_attributes` still apply to this endpoint.**

Given that multiple External Prediction Sets are being created at once, it's possible that some submissions will be successfully saved, while others will be rejected for reasons such as invalid inputs. The response from this endpoint will do two things to notify you of the success or failure of your submission:

First, the HTTP response code will be one of three values: 

Status | HTTP Response Code | Description
------ | ------------------ | -----------
OK | 200 | All External Prediction Sets in the request were successfully saved
Multi-Status | 207 | Some External Prediction Sets in the request were successfully saved, some failed
Unprocessible Entity | 422 | All External Prediction Sets in the request failed to save


Second, the response body will contain a JSON array, where each record in the array corresponds to a single forecast in your request. Successfully saved forecasts will contain the question ID and the ID of the External Prediction Set that was created for it. Forecasts that fail to save will include the question ID and an array of error messages. A `Multi-Status` response for a submission that includes 2 successful forecasts and 1 rejected forecast might look something like the example to the right.

> Multi-Status Response

```json
[
  {"id":403,"question_id":702},
  {"question_id":703,"errors":["Predictions must add up to 100%"]},
  {"id":404,"question_id":704}
]
```



> Request:

```shell
curl -X "POST" "https://yoursite.hfc-staging.com/api/v1/bulk_external_prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"external_predictor_attributes\":{\"method_name\":\"red\",\"method_type\":\"official\"},\"external_prediction_sets\":[{\"question_id\":180,\"metadata\":{\"a\":\"bcd\",\"e\":\"horse\"},\"external_predictions_attributes\":[{\"value\":0.5,\"answer_id\":540},{\"value\":0.3,\"answer_id\":541},{\"value\":0.2,\"answer_id\":542}]},{\"question_id\":181,\"metadata\":{\"a\":\"bcd\",\"e\":\"cow\"},\"external_predictions_attributes\":[{\"value\":0.6544,\"answer_id\":543},{\"value\":0.34,\"answer_id\":544},{\"value\":0.0056,\"answer_id\":545},{\"value\":\"0.0\",\"answer_id\":546},{\"value\":0.0,\"answer_id\":547}]},{\"question_id\":182,\"metadata\":{\"a\":\"bcd\",\"e\":\"duck\"},\"external_predictions_attributes\":[{\"value\":0.678912,\"answer_id\":548}]}]}"
```

> Request body example:

```json
{
  "external_predictor_attributes": {
    "method_name": "red",
    "method_type": "official"
  },
  "external_prediction_sets": [
    {
      "question_id": 180,
      "metadata": { "a": "bcd", "e": "horse" },
      "external_predictions_attributes": [
        { "value": 0.5, "answer_id": 540 },
        { "value": 0.3, "answer_id": 541 },
        { "value": 0.2, "answer_id": 542 }
      ]
    },
    {
      "question_id": 181,
      "metadata": { "a": "bcd", "e": "cow" },
      "external_predictions_attributes": [
        { "value": 0.6544, "answer_id": 543 },
        { "value": 0.34, "answer_id": 544 },
        { "value": 0.0056, "answer_id": 545 },
        { "value": "0.0", "answer_id": 546 },
        { "value": 0, "answer_id": 547 }
      ]
    },
    {
      "question_id": 182,
      "metadata": { "a": "bcd", "e": "duck" },
      "external_predictions_attributes": [
        { "value": 0.678912, "answer_id": 548 }
      ]
    }
  ]
}
```


> Response:

```json
[
  {"id":56,"question_id":219},
  {"id":57,"question_id":220},
  {"id":58,"question_id":221}
]
```

### HTTP Request

`POST https://yoursite.hfc-staging.com/api/v1/bulk_external_prediction_sets`