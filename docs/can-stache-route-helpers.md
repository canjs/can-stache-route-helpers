@module {undefined} can-stache-route-helpers
@parent can-views
@collection can-core
@package ../package.json

@description Adds routeUrl and routeCurrent helpers to stache.

@type {undefined}

  The can-stache-route-helpers module doesn't export anything; It mixes in the following [can-stache] helpers that use [can-route]:

  - [can-stache-route-helpers.routeUrl]
    Use the `routeUrl` helper like:

    ```html
    <a href='{{ routeUrl(page="recipe" id=5) }}'>{{recipe.name}}</a>
    ```

    This produces (with no pretty routing rules):

    ```html
    <a href='#!&page=recipe&id=5'>{{recipe.name}}</a>
    ```

  - [can-stache-route-helpers.routeCurrent]
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
