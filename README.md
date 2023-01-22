# StatelessSession
This library that allows Telegram Bots (or any stateless connection) to have short term memory without using database access.


## Installation
This project using composer.
```
$ composer require okayinc/stateless_session
```

## How to Use it?

```php
<?php
use OKayInc;
$session_id = md5($from_user_id.'@'.$chat_id);  // something unique
\OKayInc\StatelessSession::start($session_id);

// To restart the session (forget the pass)
\OKayInc\StatelessSession::reset();

// To get/remember a value in different HTTP sessions. If $index does not exist, $default_value is returned. 
// $default_value is optional, if omited, NULL is used insted. 
$setup_step = \OKayInc\StatelessSession::get($index, $default_value);

// To set $index to $value
\OKayInc\StatelessSession::set($index, $value);
```

Where:
* setup_step is something you want to remember between HTTP calls
* value is the actual value to remember
