# google-scholar #

nodejs module for searching google scholar

## getting started ##

1. `npm install google-scholar --save`
2. require the module `const scholar = require('google-scholar')`
3. get searching!

```
'use strict'

let scholar = require('google-scholar')

/* All of these options are passable, but only 'query' is mandatory */
scholar.search({
	query: 'Search',
	options: 'site:usp.br',
	include_citations: false,
	year_range: [2006, 2010],
	language: 'pt'
})
  .then(resultsObj => {
    console.log(resultsObj)
  })
```

## resultsObj ##

* `count`: the approximate number of results Google Scholar found for your query (the last page's results object contains the precise number)
* `results`: an array of result objects
    - the `result` abject has several fields:
        - `title`
        - `url`
        - `authors` (each author object has a `name` and a `url`)
        - `description`
        - `citedCount`
        - `citedUrl`
        - `relatedUrl`
		- `information`
* `nextUrl`: the URL for the next set of results from google scholar
* `prevUrl`: the URL for the previous set of results from google scholar
* `next`: function that returns a promise which will resolve to a `resultsObj` containing the next results
* `previous`: function that returns a promise which will resolve to a `resultsObj` containing the previous results
