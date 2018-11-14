
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
        "worker_id": "CL_DCJ82JDFK"
      }
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
        "worker_id": "CL_JKJ88IUFL"
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
