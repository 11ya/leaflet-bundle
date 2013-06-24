## Current Version

This bundle allow usage any version of library that you wish. Original lib uses as a package with forced version and original files is symlinked.

Just go to https://github.com/Leaflet/Leaflet and check tags.

## Installation

### Add bundle to your composer.json file

Set needed version and branch in `version` and `reference` of package.

``` js
// composer.json

{
    "repositories": {
        // ...

        "leaflet/leaflet": {
            "type": "package",
            "package": {
                "name": "leaflet/leaflet",
                "version": "0.5.1",
                "source": {
                    "url": "https://github.com/Leaflet/Leaflet.git",
                    "type": "git",
                    "reference": "tags/v0.5.1"
                }
            }
        }
    },

    // ...

    "require": {
		// ...
        "fanforfun/leaflet-bundle": "dev-master"
    }
}
```

### Add bundle to your application kernel

``` php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Fanforfun\LeafletBundle\FanforfunLeafletBundle(),
        // ...
    );
}
```

### Download the bundle using Composer

``` bash
$ php composer.phar update fanforfun/leaflet-bundle
```

### Install assets

Given your server's public directory is named "web", install the public vendor resources

``` bash
$ php app/console assets:install web
```

Optionally, use the --symlink attribute to create links rather than copies of the resources

``` bash
$ php app/console assets:install --symlink web
```

## Usage

Refer to the desired files in your twig/HTML template, e.g.

``` html
{% javascripts output='resources/js/*.js' '@FanforfunLeafletBundle/Resources/public/js/leaflet.js' %}
    <script type="text/javascript" src="{{ asset_url }}"></script>
{% endjavascripts %}
```

or obfuscated version

``` html
{% javascripts output='resources/js/*.js' '@FanforfunLeafletBundle/Resources/public/js/leaflet.min.js' %}
    <script type="text/javascript" src="{{ asset_url }}"></script>
{% endjavascripts %}
```

And stylesheets:

``` html
{% stylesheets filter='cssrewrite' output='resources/css/*.css' 'bundles/fanforfunleaflet/css/leaflet.css' %}
    <link href="{{ asset_url }}" rel="stylesheet" type="text/css" />
{% endstylesheets %}
{% stylesheets filter='cssrewrite' output='resources/css/*.css' 'bundles/fanforfunleaflet/css/leaflet.ie.css' %}
    <link href="{{ asset_url }}" rel="stylesheet" type="text/css" />
{% endstylesheets %}
```

## Licenses

Refer to the source code of the included files for license information

## References

1. http://symfony.com/

2. https://github.com/Leaflet/Leaflet

3. http://leafletjs.com