!!! warning "OSM API v0.6 on wiki is made by users (not admins)."
    Please note that even a **source for this documentation** is [^^not an official documentation^^](https://github.com/openstreetmap/openstreetmap-website/commit/b9c85c269726faad3c2613b37f01683c8b59f5c6#commitcomment-125789988){:target="_blank"}(1).
    { .annotate }
    
    1. :facepalm: Documented there behaviors [^^may change in the future^^](https://github.com/openstreetmap/openstreetmap-website/commit/b9c85c269726faad3c2613b37f01683c8b59f5c6#commitcomment-125789640){:target="_blank"}.

!!! success "OSM API source code"
    The code powering the API can be found on [^^GitHub^^](https://github.com/openstreetmap/openstreetmap-website/tree/master/app/controllers/api){:target="_blank"}.

!!! note "OSM API source code with CGI"
    Some of the API calls on osm.org are handled by CGImap and its source code is also available on [^^GitHub^^](https://github.com/zerebubuth/openstreetmap-cgimap){:target="_blank"}.

This Editing API is based on the ideas of the RESTful API. Requests to modify the database are authorized using or [**OAuth**](https://wiki.openstreetmap.org/wiki/OAuth){:target="_blank"}(1).
{ .annotate }

1. Read requests **do not** require authorization (except user details).