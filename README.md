# phpList REST API swagger-ui
OpenAPI Documentation for [phpList/rest-api](github.com/phpList/rest-api) ove Swaggger UI

# Updating

We use`swagger-ui-dist` which is the compiled version of swagger UI for server side projects. It's simply a copy of the `dist` directory from the [Swagger UI Repo](https://github.com/swagger-api/swagger-ui)) stored. 

So if there are updates in the UI we would like to have, the fastest way to update our copy of swagger UI would be to clone the entire swagger UI [repository](https://github.com/swagger-api/swagger-ui) and copy the contents of `dist` to `public/docs` and make the required changes in `index.html`. That includes making sure the assets (javascript and css) are pointing to the right place (`/restapi-docs/`) and that `SwaggerUIBundle` is referencing `/restapi-docs/restapi.json` correctly as shown bellow;

```js
    window.onload = function() {
      // Begin Swagger UI call region
      const ui = SwaggerUIBundle({
        url: "/restapi-docs/restapi.json",
        dom_id: '#swagger-ui',
        deepLinking: true,
        presets: [
          SwaggerUIBundle.presets.apis,
          SwaggerUIStandalonePreset
        ],
        plugins: [
          SwaggerUIBundle.plugins.DownloadUrl
        ],
        layout: "StandaloneLayout"
      });
      // End Swagger UI call region

      window.ui = ui;
    };
```
