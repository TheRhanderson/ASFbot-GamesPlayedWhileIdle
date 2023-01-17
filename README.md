GamesPlayedWhileIdle
=========
API that overrides the current list of the 'GamesPlayedWhileIdle' property of the specified ASF bot file.
This is only intended for private use. For bigger projects use this only as an example to build your own.

Features
--------
* Easy solution
* Easy integration
* Quickly changes the appID's list.

Requires
--------
* PHP >= 5.4


Code preview
-----
```php
<?php

// Get bot name from url parameter 'botname='
$botname = ($_GET[("botname")]);

// Get bot name from url parameter 'appidlist='
$appids = ($_GET[("appidlist")]);

    // Get bot file text
    $botjson = file_get_contents("/home/user/ASF/config/{$botname}.json"); 

    // Decode Bot file JSON
    $botdecoded = json_decode($botjson, true);

    // Prepare appid list
    $IDList = array_map('intval', explode(',',$appids));

    // Set appid list to 'GamesPlayedWhileIdle' array from bot file json.
    $botdecoded['GamesPlayedWhileIdle'] = $IDList;

    // Save new changes to a new string.
    $botjson = json_encode($botdecoded, JSON_UNESCAPED_UNICODE | JSON_PRETTY_PRINT);
    // Save changes to file, finally.
    file_put_contents("/home/ubuntu/ASF/config/{$botname}.json", $botjson);

    // Print confirmation message.
    echo('success');
?>
```
