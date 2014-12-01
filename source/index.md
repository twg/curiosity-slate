---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Developer Portal</a>
  - <a href='http://github.com/tripit/slate'>Slate API Documentation</a>

includes:
  - paginator
  - errors

search: true
---

# Introduction

Welcome to the Curiosity Club API! You can use our API endpoints to get information on various categories, experts, and topics in our database.

This example API documentation page was created with [Slate](http://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Categories

## Get All Categories

```shell
curl "http://api.curiosityclub.com/v1/categories"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "science",
      "label": "Science"
    },
    {
      "id": 2,
      "name": "technology",
      "label": "Technology"
    }
  ]
}
```

This endpoint retrieves all categories.

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories`

## Get a Specific Category

```shell
curl "http://api.curiosityclub.com/v1/categories/1"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "science",
    "label": "Science"
  }
}
```

This endpoint retrieves a specific category.

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories/<ID>`

### HTTP Parameters

Parameter | Description
--------- | -----------
ID | The ID of the category to retrieve

## Get Experts by Category

```shell
curl "http://api.curiosityclub.com/v1/categories/experts"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "science",
      "label": "Science",
      "experts": [
        {
            "id": 1,
            "label": "Michio Kaku"
        },
        {
            "id": 2,
            "label": "Lisa Randall"
        }
      ]
    },
    {
      "id": 1,
      "name": "technology",
      "label": "Technology",
      "experts": [
        {
            "id": 5,
            "label": "Vint Cerf"
        },
        {
            "id": 9,
            "label": "Eric Drexler"
        }
      ]
    }
  ]
}
```

This endpoint retrieves a list of experts for each category.

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories/experts`

### HTTP Response

Parameter | Description
--------- | -----------
id | Category ID
name | Category slug
label | Category display name
experts | JSON object of [Expert](#expert-http-response) details

## Get Experts for Single Category

```shell
curl "http://api.curiosityclub.com/v1/categories/<ID>/experts"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "science",
      "label": "Science",
      "experts": [
        {
            "id": 1,
            "label": "Michio Kaku"
        },
        {
            "id": 2,
            "label": "Lisa Randall"
        }
      ]
    }
  ]
}
```

This endpoint retrieves the list of experts for a specific category.

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories/<ID>/experts`

### HTTP Parameters

Parameter | Required | Description
--------- | -------- | -----------
ID | true | The ID of the category to retrieve

### HTTP Response

Parameter | Description
--------- | -----------
id | Category ID
name | Category slug
label | Category display name
experts | JSON object of [Expert](#expert-http-response) details

## Get Topics by Category

```shell
curl "http://api.curiosityclub.com/v1/categories/topics"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "science",
      "label": "Science",
      "topics": [
        {
          "id": 1,
          "name": "physics",
          "label": "Physics"
        },
        {
          "id": 2,
          "name": "space",
          "label": "Space"
        }
      ]
    },
    {
      "id": 2,
      "name": "technology",
      "label": "Technology",
      "topics": [
        {
          "id": 1,
          "name": "energy",
          "label": "Energy"
        },
        {
          "id": 2,
          "name": "robotics",
          "label": "Robotics"
        }
      ]
    }
  ]
}
```

This endpoint retrieves a list of topics for each category.

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories/topics`

## Get Topics for Single Category

```shell
curl "http://api.curiosityclub.com/v1/categories/<ID>/topics"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "science",
      "label": "Science",
      "topics": [
        {
          "id": 1,
          "name": "physics",
          "label": "Physics"
        },
        {
          "id": 2,
          "name": "space",
          "label": "Space"
        }
      ]
    }
  ]
}
```

This endpoint retrieves the list of topics for a specific category.

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories/<ID>/topics`

### HTTP Parameters

Parameter | Description
--------- | -----------
ID | The ID of the category to retrieve

# Experts

## Get All Experts

```shell
curl "http://api.curiosityclub.com/v1/experts"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
        "id": 1,
        "title": "Dr.",
        "first_name": "Michio",
        "middle_name": "",
        "last_name": "Kaku",
        "display_name": "",
        "suffix": "",
        "institution": "CUNY",
        "lower_third": ""
    },
    {
        "id": 2,
        "title": "Dr.",
        "first_name": "Lisa",
        "middle_name": "",
        "last_name": "Randall",
        "display_name": "",
        "suffix": "",
        "institution": "Harvard",
        "lower_third": ""
    }
  ],
  "paginator": {
    "total_count": 10,
    "total_pages": 5,
    "current_page": 1,
    "limit": 2
  }
}
```

This endpoint retrieves all experts.

### HTTP Request

`GET http://api.curiosityclub.com/v1/experts`

### HTTP Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
limit | false | 3 | The number of experts to retrieve on a single call
page | false | 1 | The page number to start return

### HTTP Response

Parameter | Description
--------- | -----------
id | Expert ID
title | Expert title
first_name | Expert first name
middle_name | Expert middle name
last_name | Expert last name
display_name | Expert display name
suffix | Expert suffix
institution | Expert institution
lower_third | Expert lower third

## Get a Specific Expert

```shell
curl "http://api.curiosityclub.com/v1/experts/1"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
        "id": 1,
        "title": "Dr.",
        "first_name": "Michio",
        "middle_name": "",
        "last_name": "Kaku",
        "display_name": "",
        "suffix": "",
        "institution": "CUNY",
        "lower_third": ""
    }
  ]
}
```

This endpoint retrieves a specific expert.

### HTTP Request

`GET http://api.curiosityclub.com/v1/experts/<ID>`

### HTTP Parameters

Parameter | Required | Description
--------- | -------- | -----------
ID | true | The ID of the expert to retrieve

### <a name="expert-http-response"></a>HTTP Response

Parameter | Description
--------- | -----------
id | Expert ID
title | Expert title
first_name | Expert first name
middle_name | Expert middle name
last_name | Expert last name
display_name | Expert display name
suffix | Expert suffix
institution | Expert institution
lower_third | Expert lower third

# Tags

## Get All Tags

```shell
curl "http://api.curiosityclub.com/v1/tags"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "physics",
      "label": "Physics"
    },
    {
      "id": 2,
      "name": "space",
      "label": "Space"
    }
  ],
  "paginator": {
    "total_count": 32,
    "total_pages": 16,
    "current_page": 1,
    "limit": 2
  }
}
```

This endpoint retrieves all tags.

### HTTP Request

`GET http://api.curiosityclub.com/v1/tags`

### HTTP Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
limit | false | 3 | The number of tags to retrieve on a single call
page | false | 1 | The page number to start return

### HTTP Response

Parameter | Description
--------- | -----------
id | Tag ID
name | Tag slug
label | Tag display name

## Get a Specific Tag

```shell
curl "http://api.curiosityclub.com/v1/tags/1"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "physics",
      "label": "Physics"
    }
  ]
}
```

This endpoint retrieves a specific expert.

### HTTP Request

`GET http://api.curiosityclub.com/v1/tags/<ID>`

### HTTP Parameters

Parameter | Required | Description
--------- | -------- | -----------
ID | true | The ID of the tag to retrieve

### HTTP Response

Parameter | Description
--------- | -----------
id | Tag ID
name | Tag slug
label | Tag display name