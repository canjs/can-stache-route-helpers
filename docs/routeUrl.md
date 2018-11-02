@function can-stache-route-helpers.routeUrl {{ routeUrl(hashes) }}
@parent can-stache-route-helpers

@description Returns a url using [can-route.url route.url].

@signature `routeUrl( hashes... [,merge] )`

  Calls [can-route.url route.url] with  `hashes` as its `data` argument and an
  optional `merge`. `routeUrl` can be used in conjunction with other helpers.

  This can be used on its own to create `<a>` `href`s like:

  ```html
  <mock-url></mock-url>
  <cooking-example></cooking-example>
  <script type="module">
  import {Component} from "can";
  import "//unpkg.com/mock-url@^5";

  Component.extend({
    tag: "cooking-example",
    view: `<a href='{{ routeUrl(page="recipe" id=5) }}'>{{recipe.name}}</a>`,
    ViewModel: {
      recipe: {
        default() {
          return {name: "apple pie"};
        }
      }
    }
  });
  </script>
  ```
  @codepen

  This produces (with no pretty routing rules):

  ```html
  <a href='#!&page=recipe&id=5'>{{recipe.name}}</a>
  ```

  @param {can-stache/expressions/hash} [hashes...] A hash expression like `page='edit' recipeId=id`.

  @param {Boolean} [merge] Pass `true` to create a url that merges `hashes` into the
  current [can-route] properties.  

  @return {String} Returns the result of calling `route.url`.

@signature `{{ routeUrl([merge,] hashes...) }}`

  Passes the hashes to `route.url` and returns the result.
  Using call expressions/parenthesis lets you pass the `merge` option to `route`.  This
  lets you write a url that only changes specified properties. The example below clicking __recipes__ will add a `page` hash, and clicking on the recipe name will add the `id`:

  ```html
  <mock-url></mock-url>
  <cooking-example></cooking-example>
  <script type="module">
  import {Component} from "can";
  import "//unpkg.com/mock-url@^5";

  Component.extend({
    tag: "cooking-example",
    view: `<a href='{{ routeUrl(true, page="recipes") }}'>recipes</a>
      <a href='{{ routeUrl(true, id=5) }}'>{{recipe.name}}</a>`,
    ViewModel: {
      recipe: {
        default() {
          return {name: "apple pie"};
        }
      }
    }
  });
  </script>
  ```
  @codepen

  @param {Boolean} [merge] Pass `true` to create a url that merges `hashes` into the
  current [can-route] properties.  

  @param {can-stache/expressions/hash} [hashes...] A hash expression like `page='edit' recipeId=id`.

  @return {String} Returns the result of calling `route.url`.

@body

## Use

The following demo uses `routeUrl` and [can-stache-route-helpers.routeCurrent] to
create links that update [can-route]’s `page` attribute:

@demo demos/can-stache/route-url.html

It also writes out the current url like:

```html
{{ routeUrl(undefined, true) }}
```

This calls `route.url({}, true)` which has the effect of writing out
the current url.
