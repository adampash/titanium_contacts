What is it?
-----------

A Titanium module for Android contact search because the default provided by `Ti.Contacts.getPeopleWithName` on Android searches contacts that aren't supposed to be visible (e.g., My Contacts vs. All Contacts if you sync with Google Contacts). That can cause contact searches to go *very* slowly on Android in Titanium and causes results you wouldn't expect. This lightweight only searches the appropriate contacts, and it's considerably quicker.

Usage
-----

```javascript

var contacts = require('com.adampash.contactSearch');
var contactResults = contacts.getPeopleWithName("Adam");

```

That will return an array of contacts which include only the contact's name, contact id, and optionally, the contact photo (if you want more information, you can fetch it on-demand with something like `Ti.Contacts.getPersonByID(contactResults[0].id)`.

You can also fetch images every time (which slows things down) by adding `true` as the second variable in the call:

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
