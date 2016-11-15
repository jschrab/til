# Notes on REST calls in Drupal 8

REST annotations in comments are _very_ important to allow modules/classes to define endpoints. Example:
```php

/**
 * Provides a resource to get view modes by entity and bundle.
 *
 * @RestResource(
 *   id = "custom_rest_resource",
 *   label = @Translation("Custom rest resource"),
 *   uri_paths = {
 *     "canonical" = "//api/custom"
 *   }
 * )
 */

```

Furthermore, adding an additional disambiguation line to uri_paths may be necessary to prevent conflicts with out-of-the-box RESTful Drupal 8 services.

From [drupal.org](https://www.drupal.org/docs/8/api/restful-web-services-api/restful-web-services-api-overview):

> What is very important is the @RestResource annotation's uri_paths definition. If you don't specify any, Drupal will automatically generate URI paths (and hence URLs) based on the plugin ID. If your plugin ID is fancy_todo, you'll end up with GET|PATCH|DELETE /fancy_todo/{id} and POST /fancy_todo. But, often, you'll want to specify your own paths: a canonical URI path (for example /todo/{todo_id}), but also a https://www.drupal.org/link-relations/create URI path (for example  /todo). If you only specify one of them, then the other will use the default URI path, which will then likely not match the URI path that you did specify.
So, either omit uri_paths, or specify both.

```php
/**
 * Provides a resource to get view modes by entity and bundle.
 *
 * @RestResource(
 *   id = "custom_rest_resource",
 *   label = @Translation("Custom rest resource"),
 *   uri_paths = {
 *     "canonical" = "//api/custom",
 *     "https://www.drupal.org/link-relations/create" = "//api/custom"
 *   }
 * )
 */

```

Routing annotations are a [Symfony framework convention](http://symfony.com/doc/current/bundles/SensioFrameworkExtraBundle/annotations/routing.html).

Sources:  
http://valuebound.com/resources/blog/how-to-create-custom-rest-resources-for-post-methods-drupal-8  
