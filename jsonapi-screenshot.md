# Drupal JSON:API Screenshot Sources

## Local Files Found

Two conceptual/diagram images exist in ~/Downloads/:

1. **`~/Downloads/content_migration_via_JSON_API.jpg`** - 3D illustration of JSON:API as a central hub with data pipes connecting to various services (servers, databases, laptops). Conceptual diagram, not an actual UI screenshot.

2. **`~/Downloads/simplified_circular_diagram_with_JSON_API.jpg`** - Clean circular diagram showing JSON:API at center with arrows to Mobile Apps, Websites, Feeds, Kiosks. Good for illustrating API-first architecture but not an explorer/query builder screenshot.

No relevant screenshots were found in `~/Sites/drupalorgredux/assets/` (only logos and product images).

---

## JSON:API Explorer (Official Drupal Module)

**Project page:** https://www.drupal.org/project/jsonapi_explorer

**Screenshot from drupal.org project page (best find):**
```
https://www.drupal.org/files/styles/grid-3-2x/public/project-images/explore.jsonapi.dev__location%3Dhttps%253A%252F%252Fexample.jsonapi.dev%252Fjsonapi%252Fnode%252Farticle%253Finclude%253Duid%2526fields%255Bnode--article%255D%253Ddrupal_internal__nid%252Clangcode%252Cbody%252Ctitle%20%281%29.png
```

This shows the JSON:API Explorer interface with a query for article nodes including fields like nid, langcode, body, and title.

**Live explorer app:** https://explore.jsonapi.dev/
- Single-page application for exploring any JSON:API server
- When installed as a Drupal module, available at `/jsonapi/explorer/app`
- Proxies JS/CSS assets through the Drupal site's origin

---

## JSON:API Query Builder (Contributed Module)

**Project page:** https://www.drupal.org/project/jsonapi_query_builder

**Screenshot from drupal.org project page:**
```
https://www.drupal.org/files/styles/grid-3-2x/public/project-images/2025-03-20_18-34_1.png?itok=JHr88i-4
```

This shows the visual query builder interface for constructing JSON:API requests.

---

## Postman/Browser Screenshots (DigitalNadeem Tutorial)

Source: https://www.digitalnadeem.com/drupal/how-to-configure-json-api-module-and-create-web-services-using-json-api-specifications-in-drupal/

These show actual JSON:API responses and Postman usage with Drupal:

| Image | Description |
|-------|-------------|
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/json-api-get-result.jpg | GET response - article collection |
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/sorted-created-json-Get-response.jpg | Sorted/filtered GET response |
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/post-node.jpg | POST request to create content |
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/post-response.jpg | POST response after content creation |
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/file-upload-response.jpg | File upload via JSON:API |
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/filter-multiple-conditions.jpg | Complex filtering example |
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/HTTP-authorization.jpg | Basic auth setup in Postman |
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/json-apiextras-config.jpg | JSON:API Extras configuration UI |
| https://www.digitalnadeem.com/wp-content/uploads/2020/09/json-apiextras-list-resources.jpg | Resource type listing |

---

## Running Local Drupal Site

A Lando-based Drupal site is running at `~/Sites/drupalorg`. You could potentially take a live screenshot by visiting:
- `https://drupalorg.lndo.site/jsonapi` (JSON:API entry point)
- `https://drupalorg.lndo.site/jsonapi/node/article` (example resource collection)

---

## Recommendations for the Redesign

**Best options for showing Drupal's API-first nature:**

1. **JSON:API Explorer screenshot** (from drupal.org project page) - shows the interactive explorer UI
2. **JSON:API Query Builder screenshot** (from drupal.org project page) - shows the visual query builder
3. **Postman screenshots** (from DigitalNadeem) - show real API requests/responses
4. **Local circular diagram** (`~/Downloads/simplified_circular_diagram_with_JSON_API.jpg`) - clean conceptual illustration of API-first architecture
5. **Take a fresh screenshot** from the running local Drupal site's `/jsonapi` endpoint or from https://explore.jsonapi.dev/

---

## Additional Resources

- [JSON:API Module Documentation](https://www.drupal.org/docs/core-modules-and-themes/core-modules/jsonapi-module)
- [API Overview](https://www.drupal.org/docs/core-modules-and-themes/core-modules/jsonapi-module/api-overview)
- [Fetching Resources (GET)](https://www.drupal.org/docs/core-modules-and-themes/core-modules/jsonapi-module/fetching-resources-get)
- [Filtering](https://www.drupal.org/docs/core-modules-and-themes/core-modules/jsonapi-module/filtering)
- [Ecosystem Modules](https://www.drupal.org/project/jsonapi/ecosystem)
- [Acquia: Decoupling Drupal with JSON API](https://dev.acquia.com/article/decoupling-drupal-8-json-api)
