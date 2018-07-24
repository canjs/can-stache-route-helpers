@function can-stache-route-helpers.routeCurrent {{# routeCurrent(hash) }}
@parent can-stache-route-helpers

Returns if the hash values match the [can-route]’s current properties.

@signature `routeCurrent( hashes... [,subsetMatch] )`

  Calls [can-route.isCurrent route.isCurrent] with `hashes` and returns the result. This
  can be used in conjunction with other helpers:

```html
{{linkTo("Todos", routeCurrent(page='todos' id=todo.id))}}
```

Or on its own:

```html
<a class="{{# routeCurrent(page='todos', true) }}active{{/ routeCurrent }}">Todos</a>
```

  @param {can-stache/expressions/hash} hashes A hash expression like `page='edit' recipeId=id`.

  @param {Boolean} [subsetMatch] If an optional `true` is passed, `routeCurrent` will
  return `true` if every value in `hashes` matches the current route data, even if
  the route data has additional properties that are not matched.

  @return {Boolean} Returns the result of calling [can-route.isCurrent route.isCurrent].

@signature `{{# routeCurrent([subsetMatch,] hashes...) }}FN{{else}}INVERSE{{/ routeCurrent }}`

Renders `FN` if the `hashes` passed to [can-route.isCurrent route.isCurrent] returns `true`.
Renders the `INVERSE` if [can-route.isCurrent route.isCurrent] returns `false`.

```html
<a class="{{# routeCurrent(true, page='todos') }}active{{/ routeCurrent }}">Todos</a>
```

  @param {Boolean} [subsetMatch] If an optional `true` is passed, `routeCurrent` will
  return `true` if every value in `hashes` matches the current route data, even if
  the route data has additional properties that are not matched.

  @param {can-stache/expressions/hash} hashes A hash expression like `page='edit' recipeId=id`.



  @param {can-stache.sectionRenderer} FN A subsection that will be rendered if the current route matches `hashes`.

  @param {can-stache.sectionRenderer} [INVERSE] An optional subsection that will be rendered
  if the current route does not match `hashes`.

  @return {String} The result of `SUBEXPRESSION` or `{{else}}` expression.



@body

## Use

Use the `routeCurrent` helper like:

```html
<li {{# routeCurrent(page="recipe" id=5) }}class='active'{{/ routeCurrent }}>
  <a href='{{ routeUrl(page="recipe" id=5) }}'>{{recipe.name}}</a>
</li>
```

With default routes and a url like `#!&page=recipe&id=5`, this produces:

```html
<li class='active'>
  <a href='#!&page=recipe&id=5'>{{recipe.name}}</a>
</li>
```


The following demo uses `routeCurrent` and [can-stache-route-helpers.routeUrl] to
create links that update [can-route]’s `page` attribute:

@demo demos/can-stache/route-url.html
