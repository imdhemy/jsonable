# Jsonable
Laravel JSON response trait. This trait makes it easy for any controller to return a JSON response with the appropriate HTTP status code.

## Installation
Via composer:

```
composer require imdhemy/jsonable
```

# Usage
All that you need is to `use` the `Jsonable` trait inside your controller.

**Example:**

```php
<?php
namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Imdhemy\Jsonable\Jsonable;

class CountryController extends Controller
{
    use Jsonable;

    public function index()
    {
        $data = \App\Country::get();
        return $this->ok($data, 'countries');
    }
}
```

  The previous code will return a JSON response like the following:

```json
  {
    "countries": [
        {
            "name": "Egypt",
            "capital": "Cairo",
        },
           ...
    ]
}
```

The parent key is optional, you can ommit it:

```php
$data = \App\Country::get();
return $this->ok($data);
```
The response will be like the following:

```json
[
 {
  "name": "Egypt",
  "capital": "Cairo",
  },
        ...
]
```

## Available methods

### Success Methods
| Method | Status code | Description |
|---|---|---|
|ok|200|Successful get, patch (return a JSON object)|
|created|201|Successful post (return a JSON object)|
|noContent|204|Successful delete|

### Error Status

| Method | Status code | Description |
|---|---|---|
|unauthorized|401|Not authenticated|
|invalid|403|Authenticated, but no permissions|
|notFound|404|Not Found|
|invalid|422|Validation|

### Extra methods

| Method | Status code | Description |
|---|---|---|
|accepted|202|Successful post, delete, path - async|
|badRequest|400|The request could not be understood by the server due to malformed syntax|
|paymentRequired|402|Payment required|
