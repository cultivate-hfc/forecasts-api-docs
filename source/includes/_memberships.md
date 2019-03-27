
# Memberships

## Memberships List

A list of users assigned to a given site.

> Request:

```shell
curl "https://yoursite.hfc-staging.com/api/v1/memberships" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "memberships": [
    {
      "id": 1,
      "site_id": 1,
      "site_name": "Carbon",
      "user_id": 1,
      "created_at": "2015-08-04T00:21:34.623Z",
      "updated_at": "2015-08-04T00:21:34.651Z",
      "user": {
        "key": "CEJGB744-F89M-UU4C-BC04-357B1D2421738",
        "worker_id": "CL_JKJ88IUFL",
        "demographic_info": {
          "gender": "Male",
          "education": "Bachelor's degree",
          "birth_year": "1994"
        }
      },
      "survey_responses": [
          {
            "id": 1,
            "user_id": 2,
            "survey_id": 1,
            "created_at": "2018-11-08T17:52:21.118Z",
            "updated_at": "2018-11-08T17:52:21.118Z",
            "status": "started",
            "page_order": ["1","2"],
            "survey_name": "survey-1",
            "survey_question_responses": [
              {
                "id": 1,
                "survey_question_id": 1,
                "survey_answer_id": 9,
                "survey_response_id": 1,
                "created_at": "2018-11-08T17:52:21.165Z",
                "updated_at": "2018-11-08T17:52:21.165Z",
                "question_content": "question-content-1",
                "answer_content": "abcdef",
                "survey_question_scoring_notes": "all answers get two points",
                "survey_question_scoring_scale": "a=1, b=2, c=3",
                "survey_question_correct_answer": "abcdef"
              },
              {
                "id": 2,
                "survey_question_id": 2,
                "survey_answer_id": 10,
                "survey_response_id": 1,
                "created_at": "2018-11-08T17:52:41.165Z",
                "updated_at": "2018-11-08T17:52:41.165Z",
                "question_content": "question-content-2",
                "answer_content": "this is my answer",
                "survey_question_scoring_notes": "the correct answer is worth two points",
                "survey_question_scoring_scale": "a=1, b=2, c=3",
                "survey_question_correct_answer": "abc123"
              }
            }
          ]
    },
    {
      "id": 2,
      "site_id": 1,
      "site_name": "Carbon",
      "user_id": 2,
      "created_at": "2015-08-04T00:21:34.623Z",
      "updated_at": "2015-08-04T00:21:34.651Z",
      "user": {
        "key": "AB1GB745-F76J-QU4W-BU04-357B1D2421920",
        "worker_id": "CL_DCJ82JDFK"
      },
      "survey_responses": []
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.hfc-staging.com/api/v1/memberships`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
include_profile_question_responses | false | Passing "true" for this value will include profile questions and responses for each membership.
include_survey_responses | false | Passing "true" for this value will include survey response data for each membership.
created_before | none | Returns only memberships created before the passed time. Time should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only memberships created after the passed time. Time should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only memberships update before the passed time. Time should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only memberships update after the passed time. Time should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the membership
site_id | integer | The id of the site that this membership belongs to
site_name | string | The name of the site that this membership belongs to
user_id | integer | The id of the user that this membership belongs to
user.key | string | A unique key assigned to the user, used for added authentication/authorization
user.worker_id | string | The user's worker ID
user.demographic_info | hash | Birth year, gender, and education level of the user

### Survey Response Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the survey response
user_id | integer | The id of the user that this survey response belongs to
survey_id | integer | The id of the survey that this survey response belongs to
status | string | The completion status of this membership's training assignment. Can be "started" or "completed"
page_order | array | A list showing the order in which survey pages are shown the user, based on  survey page ids
survey_name | string | The name of the survey that this response belongs to

### Survey Question Response Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the survey question response
survey_question_id | integer | The id of the survey question this survey question response belongs to
survey_answer_id | integer | The id of the survey answer this survey question response belongs to
survey_response_id | integer | The id of the survey response this survey question response belongs to
question_content | string | The content of the survey question this survey question response belongs to
answer_content | string | The answer content for this survey question response. Format varies based on the type of survey questions.
survey_question_scoring_notes | string | scoring notes for the survey question this response belongs to
survey_question_scoring_scale | string | the scoring scale for the survey question, if one exists
survey_question_correct_answer | string | the correct answer for the survey question this response belongs to