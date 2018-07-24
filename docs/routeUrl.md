@function can-stache-route-helpers.routeUrl {{ routeUrl(hashes) }}
@parent can-stache-route-helpers

Returns a url using [can-route.url route.url].

@signature `routeUrl( hashes... [,merge] )`

Calls [can-route.url route.url] with  `hashes` as its `data` argument and an
optional `merge`.

This can be used on its own to create `<a>` `href`s like:

```html
<a href="{{ routeUrl(page='todos' id=todo.id) }}">details</a>
```

Or in conjunction with other helpers:

```html
{{ makeLink( "details", routeUrl(page='todos', true) ) }}
```

@signature `{{ routeUrl([merge,] hashes...) }}`

Passes the hashes to `route.url` and returns the result.

```html
<a href="{{ routeUrl(page='todos' id=todo.id) }}">details</a>
```

@param {Boolean} [merge] Pass `true` to create a url that merges `hashes` into the
current [can-route] properties.  

@param {can-stache/expressions/hash} [hashes...] A hash expression like `page='edit' recipeId=id`.

@return {String} Returns the result of calling `route.url`.

@body

## Use

Use the `routeUrl` helper like:

```html
<a href='{{ routeUrl(page="recipe" id=5) }}'>{{recipe.name}}</a>
```

This produces (with no pretty routing rules):

```html
<a href='#!&page=recipe&id=5'>{{recipe.name}}</a>
```

Using call expressions/parenthesis lets you pass the `merge` option to `route`.  This
lets you write a url that only changes specified properties:

```html
<a href='{{ routeUrl(id=5, true) }}'>{{recipe.name}}</a>
```




The following demo uses `routeUrl` and [can-stache-route-helpers.routeCurrent] to
create links that update [can-route]’s `page` attribute:

@demo demos/can-stache/route-url.html

It also writes out the current url like:

```html
{{ routeUrl(undefined, true) }}
```

This calls `route.url({}, true)` which has the effect of writing out
the current url.
