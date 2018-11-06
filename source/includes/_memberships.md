
# Memberships

## Memberships List

Each user in Cultivate Forecasts has a single user record & user_id. However, a user can be a member of multiple sites. A membership record associates a user to a site. This endpoint provides a list of membership records for a given site and embeds the user record within each membership.

This endpoint is only accessible to site administrators.

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
      "user_id": 1,
      "created_at": "2015-08-04T00:21:34.623Z",
      "updated_at": "2015-08-04T00:21:34.651Z",
      "avatar": "ident/default_avatars/level-1-1.png",
      "role": "admin",
      "user": {
        "id": 1,
        "email": "user@example.com",
        "created_at": "2015-08-04T00:21:34.524Z",
        "updated_at": "2015-08-07T00:33:33.969Z"
      }
    },
    {
      "id": 2,
      "site_id": 1,
      "user_id": 2,
      "created_at": "2015-08-04T00:21:34.948Z",
      "updated_at": "2015-08-04T00:21:37.438Z",
      "avatar": "ident/default_avatars/level-0-1.png",
      "role": "user",
      "user": {
        "id": 2,
        "email": "user2@example.com",
        "created_at": "2015-08-04T00:21:34.924Z",
        "updated_at": "2015-08-04T00:21:34.924Z"
      }
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
update_before | none | Returns only memberships update before the passed time. Time should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
update_after | none | Returns only memberships update after the passed time. Time should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the membership
site_id | integer | The id of the site that this membership belongs to
site_name | string | The name of the site that this membership belongs to
user_id | integer | The id of the user that this membership belongs to
avatar_url | string | A URL containing an avatar image for the user
email_disabled | boolean | A flag for whether this membership has disabled email alerts
featured | boolean | A flag for whether this membership has been featured by the site
role | string | The role/privileges of the membership. Can be "user" or "admin"
forecasts_count | integer | The number of forecasts this membership has made
training_completed_at | datetime | The time & date at which this membership completed training
user.id | integer | The id of the user
user.email | string | The email of the user

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
survey_question_correct_answer | string | the correct answer for the survey question this response belongs to