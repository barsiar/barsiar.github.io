# About test

## Abracadabra
## Header 

## Pagination

All top-level API resources have support for bulk fetches via "list" API methods. These list API methods share a common structure, taking at least these two parameters: limit, and offset.

The response of a list API method represents a single page stream of objects. If you do not specify `offset`, you will receive the first page of this stream, containing the objects in order of creation (by id).

## Parameters

{type="full"}
limit
: `integer` **optional; default is 25**
: A limit on the number of objects to be returned, between 1 and 100.

offset
: `integer` **optional; default is 0**
: A cursor for use in pagination. If a value is provided, this will represent the number of results/objects that are skipped within the response.

<note>It is very possible that no results will be returned if you provide an offset that exceeds the number of results.</note>

## List Response Format

{type="full"}
object
: **value is `list`**
: A string describing the object type returned.

object
: **value is `list`**
: A string describing the object type returned.

url
: `string`
: The URL for accessing this list.