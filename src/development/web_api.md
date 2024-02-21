# Web APIs

Synapse X contains an API that allow you to easily make REST requests - `syn.request`.

You pass a table containing REST request properties to the function:
* `Url` - The Url for the request.
* `Method` - This is the REST request method. (`GET`, `POST`, etc)
* `Headers` - This is a table of HTTP headers to be passed to the request.
* `Cookies` - This is a table of HTTP cookies to be passed to the request.
* `Body` - This can be used within `POST` or other similar request types as a payload body.

The function will yield while the request is being preformed, and will return the following table:
* Success - If the request was successful or not.
* StatusCode - The HTTP status code of the request.
* StatusMessage - The HTTP status code converted to string form.
* Headers - The response headers of the request.
* Cookies - The response cookies of the request.
* Body - The response body of the request.

Synapse X also will add a few headers to any `syn.request` call:
* The `User-Agent` header by default will be `synx/current-version`. (`current-version` will be the current version of Synapse X.)
* A `Syn-Fingerprint` header will be added which allows you to uniquely identify Synapse X users.

An example of syn.request is shown below:

```lua
local Response = syn.request({
    Url = "https://example.com",
    Method = "GET"
})

print(Response.Body)
```

The HTML for [https://example.com](https://example.com) will be printed out.

## Conclusion

This concludes the Synapse X development tutorial. If you have any suggestions for topics to be included within the tutorial, please reach out to us! The next section will be a reference for all Synapse X API functions.