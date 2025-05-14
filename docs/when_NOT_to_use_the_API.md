The API is primarily intended **for editing**. For read-only purposes or projects, see [^^OSM API policies^^](https://operations.osmfoundation.org/policies/api/){:target="blank"}.

!!! danger "For bulk upload scripts or data modification, the direct API use may not be the proper mechanism"
    The modern version of creating a bulk upload or modification script is to build a changeset, load it into an editor like JOSM, and verify the work prior to commit.
     
You can also use the API to upload a [changeset](general_information/changesets.md) in an atomic manner.