@module can-stache-route-helpers
@parent can-views
@collection can-core
@package ../package.json

@body
## can-stache-route-helpers

Adds [can-stache] helpers that use [can-route].

## routeUrl
Use the `routeUrl` helper like:

```
<a href='{{routeUrl(page="recipe" id=5)}}'>{{recipe.name}}</a>
```

This produces (with no pretty routing rules):

```
<a href='#!&page=recipe&id=5'>{{recipe.name}}</a>
```

## routeCurrent
Use the `routeCurrent` helper like:

```
<li {{#routeCurrent(page="recipe" id=5)}}class='active'{{/routeCurrent}}>
  <a href='{{routeUrl(page="recipe" id=5)}}'>{{recipe.name}}</a>
</li>
```

With default routes and a url like `#!&page=recipe&id=5`, this produces:

```
<li class='active'>
  <a href='#!&page=recipe&id=5'>{{recipe.name}}</a>
</li>
```
