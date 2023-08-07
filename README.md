# clover-to-cobertura
Clover XML to Cobertura XML for Gitlab Coverage Visualization
Forked from https://github.com/ngyuki/clover-to-cobertura/tree/master

## Install

```sh
composer require --dev ngyuki/clover-to-cobertura
```

## Usage

```sh
php clover-to-cobertura < clover.xml > cobertura.xml
```

## Example for Gitlab CI

```
# .gitlab-ci.yml

image: ngyuki/php-dev

stages:
  - test

test:
  stage: test
  only:
    - merge_requests
  script:
    - composer install --no-progress --ansi
    - ./vendor/bin/phpunit --coverage-clover=coverage.clover.xml
    - ./vendor/bin/clover-to-cobertura < coverage.clover.xml > cobertura.xml
  artifacts:
    reports:
      cobertura: cobertura.xml
```

## License

- [MIT License](http://www.opensource.org/licenses/mit-license.php)
