# Web Cache

This stands between the client and the original server. This cache stores static resources like HTML, Headers etc. So whenever a client wants to access this static resource, it doesn't directly requests the server but the Cache directly gives the response to the client, making data transmission faster(Cache hit).

Some predefined rules are set as to what can be put in the web cache.

<mark>Caching comes in one of the methods used in CDNs(Content Delivery Networks)</mark>

Whenever a request is made by the client, static resource, the web cache creates a **cache key** which consists of usual parameters, so if in future same request is made, it will generate a cache key, so if it matches the previous key, it sends the data.

**Dynamic Info** is not stored in cache acc to cache rules, as it can contain sensitve info.

## Some rules for caching

* Static file extensions like `.js` or `.css` .

* Static directory rules which are rarely changed like `/static` and `/assets`.

