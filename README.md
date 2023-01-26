# Test with Psalm Phar (*with* plugins)

Using the setup described here: <https://andreas.heigl.org/2023/01/26/use-phars-along-with-composer/>

```shell
composer install
./tools/psalm
php src/index.php
```

This is what I get:

```
❯ ./tools/psalm
Target PHP version: 8.2 (inferred from current PHP version) Enabled extensions: .
Scanning files...
Uncaught TypeError: Psalm\PhpUnitPlugin\Hooks\TestCaseHandler::hasInitializers(): Argument #2 ($stmt) must be of type PhpParser\Node\Stmt\ClassLike, _HumbugBox1cb33d1f20f1\PhpParser\Node\Stmt\Interface_ given, called in /repos/tools-test/vendor/psalm/plugin-phpunit/src/Hooks/TestCaseHandler.php on line 84 and defined in /repos/tools-test/vendor/psalm/plugin-phpunit/src/Hooks/TestCaseHandler.php:514
Stack trace:
#0 /repos/tools-test/vendor/psalm/plugin-phpunit/src/Hooks/TestCaseHandler.php(84): Psalm\PhpUnitPlugin\Hooks\TestCaseHandler::hasInitializers(Object(Psalm\Storage\ClassLikeStorage), Object(_HumbugBox1cb33d1f20f1\PhpParser\Node\Stmt\Interface_))
#1 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/EventDispatcher.php(303): Psalm\PhpUnitPlugin\Hooks\TestCaseHandler::afterClassLikeVisit(Object(Psalm\Plugin\EventHandler\Event\AfterClassLikeVisitEvent))
#2 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/PhpVisitor/ReflectorVisitor.php(354): Psalm\Internal\EventDispatcher->dispatchAfterClassLikeVisit(Object(Psalm\Plugin\EventHandler\Event\AfterClassLikeVisitEvent))
#3 phar:///repos/tools-test/tools/psalm/vendor/nikic/php-parser/lib/PhpParser/NodeTraverser.php(202): Psalm\Internal\PhpVisitor\ReflectorVisitor->leaveNode(Object(_HumbugBox1cb33d1f20f1\PhpParser\Node\Stmt\Interface_))
#4 phar:///repos/tools-test/tools/psalm/vendor/nikic/php-parser/lib/PhpParser/NodeTraverser.php(85): _HumbugBox1cb33d1f20f1\PhpParser\NodeTraverser->traverseArray(Array)
#5 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/Scanner/FileScanner.php(51): _HumbugBox1cb33d1f20f1\PhpParser\NodeTraverser->traverse(Array)
#6 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/Codebase/Scanner.php(398): Psalm\Internal\Scanner\FileScanner->scan(Object(Psalm\Codebase), Object(Psalm\Storage\FileStorage), false, Object(Psalm\Progress\DefaultProgress))
#7 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/Codebase/Scanner.php(547): Psalm\Internal\Codebase\Scanner->scanFile('phar:///repos...', Array, true)
#8 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/Codebase/Scanner.php(310): Psalm\Internal\Codebase\Scanner->scanAPath(1, 'phar:///repos...')
#9 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/Codebase/Scanner.php(220): Psalm\Internal\Codebase\Scanner->scanFilePaths(1)
#10 phar:///repos/tools-test/tools/psalm/src/Psalm/Codebase.php(377): Psalm\Internal\Codebase\Scanner->scanFiles(Object(Psalm\Internal\Codebase\ClassLikes), 1)
#11 phar:///repos/tools-test/tools/psalm/src/Psalm/Config.php(1640): Psalm\Codebase->scanFiles()
#12 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/Analyzer/ProjectAnalyzer.php(446): Psalm\Config->visitStubFiles(Object(Psalm\Codebase), Object(Psalm\Progress\DefaultProgress))
#13 phar:///repos/tools-test/tools/psalm/src/Psalm/Internal/Cli/Psalm.php(272): Psalm\Internal\Analyzer\ProjectAnalyzer->check('/repos...', true)
#14 phar:///repos/tools-test/tools/psalm/psalm(7): Psalm\Internal\Cli\Psalm::run(Array)
#15 /repos/tools-test/tools/psalm(14): require('phar:///repos...')
#16 {main}
(Psalm 5.6.0@e784128902dfe01d489c4123d69918a9f3c1eac5 crashed due to an uncaught Throwable)
```
