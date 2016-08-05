All API URLs listed here must be prefixed by the root API URL, such as http://www.mysite.com/phplicengine/api

Service class:
```php
$api = new \PHPLicengine\Service\License($base_url, $api_key);
```

#### POST /license/add - Add License (v2.?.?)

e.g. http://www.mysite.com/phplicengine/api/license/add

Service method:
```php
$productId = 2; // required.

$response = $api->addLicense($license);
```

Sample:

```php
use PHPLicengine\Service\License;
$base_url = "http://www.mysite.com/phplicengine"; // no trailing slash!
$api_key = "API key goes here";
try {
     $api = new License ($base_url, $api_key);
     $response = $api->addLicense($productId);
     if ($response->isError()) { // if response of api has error
         print($response->getErrorMessage());
     } else {
         // $dataAsObject = $response->getDecodedJson();
         // echo $response->getReference();
         print_r($response->getJsonAsArray());
     }
} catch (\Exception $e) {
     echo $e->getMessage();
}
```

Response (if license type is remote):

```
Array
(
    [orderId] => 1
    [status] => 0
    [locked] => 0
    [domainName] => 
    [secureDomainName] => 
    [licenseKey] => 0E64E718BD11A0A8289843A10ED4C9D8
    [brand] => 0
    [orderedOn] => 1470435858
    [expiryOn] => never
    [optVal1] => foo
    [optVal2] => bar
    [optVal3] => 
    [optVal4] => 
    [optVal5] => 
    [ip] => 
)
```

Response (if license type is ionCube):

```
Array
(
    [orderId] => 
    [status] => 0
    [locked] => 0
    [domainName] => 
    [secureDomainName] => 
    [macinfo] => 
    [orderedOn] => 1470435945
    [expiryOn] => 1470597052
    [optVal1] => 
    [optVal2] => 
    [optVal3] => 
    [optVal4] => 
    [optVal5] => 
    [ip] => 
)
```

#### POST /license/change/status - Change License Status (v2.?.?)

0 = pending, 1 = active

Service method:
```php
$response = $api->changeLicenseStatus($productId, "active");
```

Respnse:
```
{"message":"success"}
```