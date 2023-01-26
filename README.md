# Test with composer-bin-plugin

```shell
composer install
./vendor-bin/psalm/vendor/bin/psalm
php src/index.php
```

This is what I get:

```
❯ ./vendor-bin/psalm/vendor/bin/psalm

Fatal error: Cannot redeclare Amp\delay() (previously declared in /repos/tools-test/vendor/amphp/amp/src/functions.php:64) in /repos/tools-test/vendor-bin/psalm/vendor/amphp/amp/lib/functions.php on line 131

Call Stack:
    0.0001     497128   1. {main}() /repos/tools-test/vendor-bin/psalm/vendor/bin/psalm:0
    0.0002     498216   2. include('/repos/tools-test/vendor-bin/psalm/vendor/vimeo/psalm/psalm') /repos/tools-test/vendor-bin/psalm/vendor/bin/psalm:120
    0.0016     828632   3. Psalm\Internal\Cli\Psalm::run($argv = [0 => './vendor-bin/psalm/vendor/bin/psalm']) /repos/tools-test/vendor-bin/psalm/vendor/vimeo/psalm/psalm:9
    0.0017     831720   4. Psalm\Internal\IncludeCollector->runAndCollect($f = class Closure { public $static = ['current_dir' => '/repos/tools-test/', 'options' => [...], 'vendor_dir' => 'vendor'] }) /repos/tools-test/vendor-bin/psalm/vendor/vimeo/psalm/src/Psalm/Internal/Cli/Psalm.php:220
    0.0017     831936   5. Psalm\Internal\Cli\Psalm::Psalm\Internal\Cli\{closure:/repos/tools-test/vendor-bin/psalm/vendor/vimeo/psalm/src/Psalm/Internal/Cli/Psalm.php:223-225}() /repos/tools-test/vendor-bin/psalm/vendor/vimeo/psalm/src/Psalm/Internal/IncludeCollector.php:35
    0.0017     831936   6. Psalm\Internal\CliUtils::requireAutoloaders($current_dir = '/repos/tools-test/', $has_explicit_root = FALSE, $vendor_dir = 'vendor') /repos/tools-test/vendor-bin/psalm/vendor/vimeo/psalm/src/Psalm/Internal/Cli/Psalm.php:224
    0.0023     986416   7. require_once('/repos/tools-test/vendor-bin/psalm/vendor/autoload.php') /repos/tools-test/vendor-bin/psalm/vendor/vimeo/psalm/src/Psalm/Internal/CliUtils.php:132
    0.0023     992368   8. ComposerAutoloaderInit8b32789b100d847470e5e56a7a899b6b::getLoader() /repos/tools-test/vendor-bin/psalm/vendor/autoload.php:25
    0.0028    1090688   9. ComposerAutoloaderInit8b32789b100d847470e5e56a7a899b6b::{closure:/repos/tools-test/vendor-bin/psalm/vendor/composer/autoload_real.php:35-41}($fileIdentifier = 'e8aa6e4b5a1db2f56ae794f1505391a8', $file = '/repos/tools-test/vendor-bin/psalm/vendor/composer/../amphp/amp/lib/functions.php') /repos/tools-test/vendor-bin/psalm/vendor/composer/autoload_real.php:43
```
