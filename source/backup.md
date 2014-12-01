---
title: API Reference

language_tabs:
  - shell
  - php
  - ruby
  - python

toc_footers:
  - <a href='#'>Developer Portal</a>
  - <a href='http://github.com/tripit/slate'>Slate API Documentation</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, PHP, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](http://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```php
<?php
include 'curiosityclub.php';

$api = $curiosityclub->authorize('meowmeowmeow');
?>
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace `meowmeowmeow` with your personal API key.
</aside>

# Categories

## Get All Categories

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```php
<?php
include 'curiosityclub.php';

$api = $curiosityclub->authorize('meowmeowmeow');
$api->categories->get();
?>
```

```shell
curl "http://api.curiosityclub.com/v1/categories"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "science",
    "label": "Science"
  },
  {
    "id": 2,
    "name": "technology",
    "label": "Technology"
  },
  {
    "id": 3,
    "name": "civilization",
    "label": "Civilization"
  },
  {
    "id": 4,
    "name": "human_spirit",
    "label": "Human Spirit"
  }
  ]
```

This endpoint retrieves all categories.

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Category

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```php
<?php
include 'curiosityclub.php';

$api = $curiosityclub.authorize('meowmeowmeow');
$api->categories->get(1);
?>
```

```shell
curl "http://api.curiosityclub.com/v1/categories/1"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "science",
  "label": "Science"
}
```

This endpoint retrieves a specific category.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the category to retrieve

## Get Experts by Category

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories/experts`

## Get Experts for Single Category

### HTTP Request

`GET http://api.curiosityclub.com/v1/categories/<ID>/experts`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the category to retrieve

