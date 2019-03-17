
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

| Method          | Status           | Description  |
| :--------------- |:---------------- | :-----------------|
| **ok**        | 200    | The request has succeeded. The information returned with the response is dependent on the method used in the request. |
| **created** | 201      |   The request has been fulfilled and resulted in a new resource being created.
| **accepted** | 202      |    The request has been accepted for processing, but the processing has not been completed. |
| **badRequest**       | 400    | The request could not be understood by the server due to malformed syntax. The client SHOULD NOT repeat the request without modifications. |
| **unauthorized** | 401      |   The request requires user authentication. |
| **paymentRequired** | 402      |    The original intention was that this code might be used as part of some form of digital cash or micropayment scheme, but that has not happened, and this code is not usually used. |
| **forbidden**        | 403 | The server understood the request, but is refusing to fulfill it. Authorization will not help and the request SHOULD NOT be repeated. |
| **notFound** | 404 |   The server has not found anything matching the Request-URI. No indication is given of whether the condition is temporary or permanent. |
| **invalid** | 422      |    The server understands the content type of the request entity, and the syntax of the request entity is correct, but was unable to process the contained instructions. |


## Hire me
I’m a freelance fullstack developer, trainer and speaker based in Egypt, working with companies across the globe. I partner with different developers and teams to execute and build beautiful, robust, secure Web Applications and Mobile Applications (iOS and Android) using the latest engineering techniques. [Learn more about my experience.](http://www.dhemy.studio/#experience)
