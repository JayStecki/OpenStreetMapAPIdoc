The API (live-api) is currently accessible using the following URL:

[See the live-api :material-map-outline:](https://api.openstreetmap.org){ target=_blank .md-button }

When testing your software against the API you should consider using(1):
{ .annotate }

1. Your account for the live service is not in the same database, so you probably need a new username and password for the test service.

[See the dev-api :fontawesome-solid-map:](https://master.apis.dev.openstreetmap.org/){ target=_blank .md-button .md-button--primary }

All of the calls to the API which update, create or delete data have to be made by an **authenticated and authorized** user(1).
{ .annotate }

1. Authentication works by using OAuth 2.0.

## Required scopes for OAuth 2.0

The required OAuth scopes to be able to use the full API v0.6 are:

- ```read_prefs```
- ```write_prefs```
- ```write_api```
    - ```write_changeset_comments``` (currently included in write_api)
- ```read_gpx```
- ```write_gpx```
- ```write_notes```
- ```write_diary``` (supported scope by OAuth 2.0 but is not required by the API v0.6)
- ```write_redactions```
- ```write_blocks```
- ```consume_messages```
- ```send_messages```

## Error codes

HTTP status codes (400-500).

=== "400 (**Bad request**)"
    If you are accessing the cgimap version of the API, this error code will be returned when OAuth fails with a ==Bad OAuth request==.
=== "401 (**Unauthorized**)"
    Login was unsuccessful.
=== "403 (**Forbidden**)"
    Login was successful but the user is not allowed to carry out the operation. The user may have been blocked, or the OAuth application may not have been given the required permissions. An application should display the error message (which will be translated if necessary) and, if it has an end-user UI, provide an easy way to access openstreetmap.org and view any messages there.