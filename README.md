# Backdevs' PHP Coding Standard

A [PHP_CodeSniffer](https://github.com/PHPCSStandards/PHP_CodeSniffer) coding standard and other static analysis tools configuration files for Backdevs' PHP projects.

## Included default configurations
- [PHP_CodeSniffer](./phpcs/phpcs.xml)
- [PHP Mess Detector](./phpmd/phpmd.xml)

## Installation

Composer:
```shell
composer require --dev backdevs/coding-standard
```

## Usage

### PHP_CodeSniffer:

In your project's `phpcs.xml` file add the following line:
```xml
<rule ref="BackdevsCodingStandard"/>
```

If you don't have a `phpcs.xml` file, here's an example for a Laravel project:
```xml
<?xml version="1.0"?>
<ruleset
        name="Backdevs Coding Standard"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="./vendor/squizlabs/php_codesniffer/phpcs.xsd"
>
    <description>Backdevs Coding Standard.</description>
    
    <arg name="extensions" value="php"/>
    <arg name="colors" />

    <arg value="sp"/>

    <file>app</file>
    <file>bootstrap</file>
    <file>config</file>
    <file>database</file>
    <file>routes</file>
    <file>tests</file>

    <exclude-pattern>cache/*</exclude-pattern>

    <rule ref="BackdevsCodingStandard"/>
</ruleset>
```

Now you should be able to run:
```shell
vendor/bin/phpcs
```

### PHP Mess Detector:
If you don't have the `phpmd/phpmd` package installed, you can install it by running:
```shell
composer require --dev phpmd/phpmd
```

Then, in your project's `phpmd.xml` file add the following line:
```xml
<rule ref="vendor/backdevs/coding-standard/phpmd/phpmd.xml"/>
```

If you don't have a `phpmd.xml` file, here's a simple example:
```xml
<?xml version="1.0"?>
<ruleset
    name="Backdevs Coding Standard"
    xmlns="http://pmd.sf.net/ruleset/1.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://pmd.sf.net/ruleset/1.0.0 http://pmd.sf.net/ruleset_xml_schema.xsd"
    xsi:noNamespaceSchemaLocation="http://pmd.sf.net/ruleset_xml_schema.xsd"
>
    <description>Backdevs Coding Standard.</description>

    <rule ref="vendor/backdevs/coding-standard/phpmd/phpmd.xml"/>
</ruleset>
```

Now you can run:
```shell
vendor/bin/phpmd app,bootstrap,config,database,routes,tests text phpmd.xml
```
