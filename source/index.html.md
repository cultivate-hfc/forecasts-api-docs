---
title: Cultivate Forecasts API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
- pagination
- push_apis
- clarifications
- consensus_history
- external_prediction_sets
- fundamental_activity_units
- memberships_without_surveys
- prediction_sets
- questions
- scores

search: true
---


# Getting Started

Each performer will be assigned a subdomain for use in HFC. Throughout the API documentation, you'll see URL's in the format of `https://yoursite.hfc-staging.com`. Once you have your subdomain, you should replace `yoursite` with your assigned subdomain. Contact Cultivate Labs at [techsupport@hybridforecasting.com](mailto:techsupport@hybridforecasting.com) to obtain your assigned subdomain.

# Environments

## Primary Environments

Cultivate Labs will be hosting two primary environments: a staging environment and a production environment. The staging environment should be used during development and testing of your system and the production environment should be used during live forecasting.

Environment | Domain
--------- | -----------
Staging | https://yoursite.hfc-staging.com
Production | https://yoursite.hybridforecasting.com

## T&E-furnished Data Stream Environments

In addition to these two primary environments, the T&E team is providing a stream of [individual-level forecasts](#prediction-sets) and [aggregate "crowd" forecasts](#aggregate-predictions). These streams are derived from the benchmark condition. The domain used for accessing both of these API’s will use the `control` subdomain (e.g. `https://control.hybridforecasting.com`), not your assigned subdomain. 

# Authentication

Authentication in the Cultivate Forecasts API is done via OAuth. To obtain an oauth token, contact [techsupport@hybridforecasting.com](mailto:techsupport@hybridforecasting.com).

All requests to the various APIs should include your token as part of an authorization header. You can see an example curl request to the right.

```shell
curl "https://yoursite.hfc-staging.com/api/v1/me" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```
