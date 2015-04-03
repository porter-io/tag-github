# Design Goals

* A tag system that can tag anything in a realm (Github repos is our target use case for now)
* Easily merged (for collaboration)
* Easily added/modified/removed (for local operations)
* Arbitrary tag meta data
* Multiple tags on a single entity
* Maximum DRY, minimum redundancy

# Data Structure

* Tags and repos are kept in separate folders.
* Each repo/tag is a folder with a file __meta__.json containing timestamps and arbitrary data. 
* A repo is tagged by placing a relative symlink to a tag folder in its own folder. 
* Tag names must be unique. A tag can't be tagged.
* All names are case-insensitive and converted to lower case when processed.

## Tags

    root    /tags/
            /tags/language/python
            /tags/language/...
            /tags/brand/google

## Repos

    root    /repos/owner/repo/
            /repos/owner/repo/__meta__.json
            /repos/owner/repo/python             -> ../../../tags/language/python
