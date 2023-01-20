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
use okayinc;
$session_id = md5($from_user_id.'@'.$chat_id);  // something unique
okayinc\telegram_session::start($session_id);

...

// To restart the session (forget the pass)
okayinc\telegram_session::reset();

// To get/remember a value in different HTTP sessions 
$setup_step = okayinc\telegram_session::get('setup_step');

// To set a value
okayinc\telegram_session::set('setup_step', $value);
```

Where:
* setup_step is something you want to remember between HTTP calls
* value is the actual value to remember
