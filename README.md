**ARCHIVED : Qwant's API has changed a lot since the time this documentation was last updated. Any client designed following the present document will not work properly. It is to be considered outdated and invalid.**

# Qwant API docs
Welcome! Here you'll find unofficial docs for the Qwant REST API, which allows you to get web, image, news, music and more search results from the Qwant search engine.
As you can see, this is very much a work in progress, so I appreciate issues and PRs :)

## Table of Contents
- [Endpoints](#endpoints)
  - [Get search results]()

## Endpoints
### Get Qwant Search results
```
api.qwant.com/api/search/<type of search>
```
#### Parameters
##### In URL
  - `<type of search>` - determines the type of search to perform, from :
    - `web`
    - `news`
    - `images`
    - `videos`
    - `social`
    - `shopping`
##### Query Parameters
  - `uiv` - **Required**, must be `4` for the request to complete successfully (TODO : What does it mean?)
  - `q` - **Required**, the keyword(s) for the query.
  - `t` - **Seems to be required**, the type of your search (same as above)
  - `count` - **Optional**, the number of items to get. (?)Must be at most 10, what it defaults to. (TODO : Looks like this is not the case for images. Check this.)
  - `offset` - **Optional**, the offset from the first result
  - `safesearch`- **Optional**, level of content filtering (0, 1 or 2).
  - `locale` - **Optional**, the language for searching (like `fr_FR`)
  
#### Response
Returns a JSON object with the following things :
- `status` : `success` or `error` depending on if the request failed or succeded.
  - May return `success` even if there's an error (like invalid or missing parameters). You can check for `data.error_code`.
- `data` : An object containing the data resulting from the request :
  - `query` : Contains information about the query you sent :
    - `locale` : The language of the query
    - `query` : The query's search text
    - `offset` : The offset from the first search result, as in the sent query
  - `cache` : TODO, idk what this actually is.
  - `result` : The results from the search query
    - `total` : The total number of results you'd get from this particular query
    - `blacklisted` : TODO
    - `items` : An array containing the actual search results as objects :
      - `title` : Title of the search result. Contains `<b>` html tags around the searched text.
      - `favicon` : A URL to the search result's website favicon
      - `url` : The URL to the search result
      - `source` : Same as `url`, except it contains `<b>` html tags around the searched text.
      - `desc` : The description of the search result.
      - `_id` : TODO
      - `score` : TODO
      - `position` : TODO
   - `filters` : TODO
   - `lastPage` : I have no idea.
   - `ads` : Ads to be displayed before the search results. TODO
  
