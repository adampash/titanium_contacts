Usage
-----

```javascript

var contacts = require('com.adampash.contactSearch');
var contactResults = contacts.getPeopleWithName("Adam");

```

You can also optional fetch images (which slows things down) by adding `true` as the second variable in the call:

```javascript

var contacts = require('com.adampash.contactSearch');
var contactResults = contacts.getPeopleWithName("Adam", true);

```

Alternatively (and my preference, for performance), you can fetch thumbnails for contacts a la carte like so:

```javascript

var contacts = require('com.adampash.contactSearch');
var contactResults = contacts.getPeopleWithName("Adam", true);

var contact = contactResults[0];
if (contact.photo_id) {
  var imageBlob = contacts.fetchThumbnail(contact.photo_id);
}

```
