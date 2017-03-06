# silex-autoreload

[![StyleCI](https://styleci.io/repos/79909479/shield?branch=master)](https://styleci.io/repos/79909479)

AutoReload functionality service provider for [**Silex 2.0+**](http://silex.sensiolabs.org/) micro-framework.

> This project is a part of [`silex-tools`](https://github.com/lokhman/silex-tools) library.

## <a name="installation"></a>Installation
You can install `silex-autoreload` with [Composer](http://getcomposer.org):

    composer require lokhman/silex-autoreload

## <a name="documentation"></a>Documentation
Simple service provider for page auto-reload functionality. It will embed small JavaScript file into every page with
`text/html` content type, that will reload the page once any (as per configuration) file in the tree is updated.
Supports directories, file name patterns and path exclusions.

    use Lokhman\Silex\Provider\AutoReloadServiceProvider;

    $app->register(new AutoReloadServiceProvider(), [
        'autoreload.interval' => 60,
        'autoreload.uri' => '/__autoreload',
        'autoreload.js_uri' => '/__autoreload.js',
        'autoreload' => [
            'dirs' => ['/dir/to/watch1', '/dir/to/watch2'],
            'files' => ['*.twig', '*.css', '*.js'],
            'exclude' => ['node_modules'],
        ],
    ]);

Module can be switched off with setting `autoreload` parameter to `false`.

Requires [`APCu`](http://php.net/manual/en/book.apcu.php) extension enabled and
[`Symfony Finder`](https://github.com/symfony/finder) library.

## <a name="license"></a>License
Library is available under the MIT license. The included LICENSE file describes this in detail.
