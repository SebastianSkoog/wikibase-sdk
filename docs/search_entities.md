# Search entities

*associated Wikibase API doc: [wbsearchentities](https://www.wikidata.org/w/api.php?action=help&modules=wbsearchentities)*

```js
const url = wbk.searchEntities('Ingmar Bergman')
```

this returns a query url that you are then free to request with the tool you like
```
https://www.wikidata.org/w/api.php?action=wbsearchentities&search=Ingmar%20Bergman&language=en&limit=20&format=json
```

or with more parameters:
```js
const search = 'Ingmar Bergman'
const language = 'fr' // will default to 'en'
const limit = 10 // defaults to 20
const format = 'json' // defaults to json

const url = wbk.searchEntities(search, language, limit, format)
```
which can also be passed as an object:
```js
const url = wbk.searchEntities({
  search: 'Ingmar Bergman',
  format: 'xml',
  language: 'sv',
  limit: 30,
  continue: 10
})
```

By default, the `uselang` parameter (the language in which the search results are returned) is set to the same as the language passed, but if for some weird use case you need to set a different language, you can still pass a 2 letters language code:
* as last argument (inline interface)
```js
const uselang = 'eo'
const url = wbk.searchEntities(search, language, limit, format, uselang)
```
* or set `uselang` in the option object (object interface).
```js
const url = wbk.searchEntities({
  search: 'Ingmar Bergman',
  language: 'sv',
  uselang: 'eo'
})
```
If the values aren't available in the desired language, it will fallback to the English value if available.

## entities type
You can request a specific type of entity by setting the `type` parameter to either `item` (default), `property`, `lexeme`, `form`, or `sense`:
```js
const url = wbk.searchEntities({ search: 'alphabet', type: 'property' })
```
