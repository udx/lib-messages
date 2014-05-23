There is a growing need to be able to notify or engage select users in regards to certain web services. Specifically, there is often a need to notify the user while they are using their WordPress control panel - such as in the case of a third-party service requiring re-authentication from the end-user. 

Additionally, there is a growing need to keep users updated on non-critical messages related to their ongoing web services, such as data syndication. Delivering such messages over e-mail is not nearly as ideal as in the control panel where where the user take the necssary action to resolve the issue, acknowledgement a change or reject an update of some sort.

## Objectives
- Allow a standard way of pushing messages to WordPress sites over XML-RPC. 
- Allow for basic Acknowledgement, Acceptance and Rejection of messages.

## Basic Message Manipluation
```php
// Get Message by ID.
$message = new UsabilityDynamics\Message( 23454302133 );

// Mark Message as Read.
$message->read();

// Acknowledge Receipt.
$message->acknowledge();

// Archive.
$message->archive();

// Delete Permanently.
$message->delete();
```

## Message Queries
Single Messages are Post Types they have all the same searching and querying functionality as Posts and Pages.

```php
$messages = get_posts(array(
 "post_type" => "_message",
 "post_status" => "publish",
))
```

## AJAX Endpoints
Admin AJAX API calls should be used for most of the backend administration.

Get specific message as JSON object.
```GET     /wp-admin.php?action=/message/23432```

Delete a message by ID.
```DELETE  /wp-admin.php?action=/message/23432```

Perform basic search/query.
```GET     /wp-admin.php?action=/messages?q=type:critical```

Mark a message as acknowledge
```GET    /wp-admin.php?action=/message/23432/acknowledge```

Mark a message as accepted
```GET    /wp-admin.php?action=/message/23432/accept```

Mark a message as rejected
```GET    /wp-admin.php?action=/message/23432/reject```


