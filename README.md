# Qwant API docs
Welcome! Here you'll find unofficial docs for the Qwant REST API, which allows you to get web, image, news, music and more search results from the Qwant search engine.
As you can see, this is very much a work in progress, so I appreciate issues and PRs :)

## Table of Contents
1. [Endpoints](#endpoints)

## Endpoints
### Searching results, except Maps, Music or Causes results
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
  - `count` - **Optional**, the number of items to get. (TODO : What does it default to?)
  - `safesearch`- **Optional**, level of content filtering (0, 1 or 2).
  - `locale` - **Optional**, the language for searching (like `fr_FR`)
