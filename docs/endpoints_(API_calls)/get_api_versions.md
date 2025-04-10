Returns a list of available API versions supported by this instance.

## Request

**`GET`** `/api/versions`

## Response

Version number.

``` json title="apiVersion_example.json" linenums="1" hl_lines="4-5"
{
 "version": "0.6",
 "generator": "OpenStreetMap server",
 "api": {
  "versions": ["0.6"]
 }
}
```