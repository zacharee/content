---
title: 'ServiceWorkerGlobalScope: install event'
slug: Web/API/ServiceWorkerGlobalScope/install_event
page-type: web-api-event
tags:
  - API
  - Event
  - Reference
  - Service worker API
  - ServiceWorkerGlobalScope
  - install
browser-compat: api.ServiceWorkerGlobalScope.install_event
---
{{APIRef("Service Workers API")}}

The **`install`** event of the {{domxref("ServiceWorkerGlobalScope")}} interface is fired when a {{domxref("ServiceWorkerRegistration")}} acquires a new {{domxref("ServiceWorkerRegistration.installing")}} worker.

This event is not cancelable and does not bubble.

## Syntax

Use the event name in methods like {{domxref("EventTarget.addEventListener", "addEventListener()")}}, or set an event handler property.

```js
addEventListener('install', event => { });

oninstall = event => { };
```

## Event type

An {{domxref("ExtendableEvent")}}. Inherits from {{domxref("Event")}}.

{{InheritanceDiagram("ExtendableEvent")}}

## Event properties

_Doesn't implement any specific properties, but inherits properties from its parent, {{domxref("Event")}}._

## Examples

The following snippet shows how an `install` event handler can be used to populate a cache with a number of responses, which the service worker can then use to serve assets offline:

```js
this.addEventListener('install', function(event) {
  event.waitUntil(
   caches.open('v1').then(function(cache) {
      return cache.addAll([
        '/sw-test/',
        '/sw-test/index.html',
        '/sw-test/style.css',
        '/sw-test/app.js',
        '/sw-test/image-list.js',
        '/sw-test/star-wars-logo.jpg',
        '/sw-test/gallery/',
        '/sw-test/gallery/bountyHunters.jpg',
        '/sw-test/gallery/myLittleVader.jpg',
        '/sw-test/gallery/snowTroopers.jpg'
      ])
   })
   );
});
```

You can also set up the event handler using the `oninstall` property:

```js
globalScope.oninstall = function(event) {
  // ...
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("ServiceWorkerGlobalScope/activate_event", "activate")}} event
- {{domxref("ServiceWorkerGlobalScope")}}
- [Service Worker API](/en-US/docs/Web/API/Service_Worker_API)
