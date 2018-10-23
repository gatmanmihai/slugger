# Simple slugger for PHP 7.2+ based on ICU

[![Build Status](https://api.travis-ci.com/sunrise-php/slugger.svg?branch=master)](https://travis-ci.com/sunrise-php/slugger)
[![CodeFactor](https://www.codefactor.io/repository/github/sunrise-php/slugger/badge)](https://www.codefactor.io/repository/github/sunrise-php/slugger)
[![Latest Stable Version](https://poser.pugx.org/sunrise/slugger/v/stable?format=flat)](https://packagist.org/packages/sunrise/slugger)
[![Total Downloads](https://poser.pugx.org/sunrise/slugger/downloads?format=flat)](https://packagist.org/packages/sunrise/slugger)
[![License](https://poser.pugx.org/sunrise/slugger/license?format=flat)](https://packagist.org/packages/sunrise/slugger)

## Installation

```
composer require sunrise/slugger
```

## How to use

#### Russian to Latin

```php
$slugger = new \Sunrise\Slugger\Slugger();

// "syesh-yeshche-etikh-myagkikh-frantsuzskikh-bulok-da-vypey-chayu"
$slugger->slugify('Съешь ещё этих мягких французских булок, да выпей чаю');
```

#### Deutsch to Latin

```php
$slugger = new \Sunrise\Slugger\Slugger();

$slugger->setTransliteratorId('de-ASCII');

// Returns "falsches-ueben-von-xylophonmusik-quaelt-jeden-groesseren-zwerg"
$slugger->slugify('Falsches Üben von Xylophonmusik quält jeden größeren Zwerg');
```

#### Only transliteration

```php
$slugger = new \Sunrise\Slugger\Slugger();

$slugger->setTransliteratorId('Hiragana-Latin');

// Returns "irohanihoheto chirinuruwo wakayotareso tsunenaramu uwinookuyama kefukoete asakiyumemishi wehimosesu"
$slugger->transliterate('いろはにほへと ちりぬるを わかよたれそ つねならむ うゐのおくやま けふこえて あさきゆめみし ゑひもせす', '');
```

#### Customization

```php
$slugger = new \Sunrise\Slugger\Slugger();

$slugger->setTransliteratorId('Greek-Latin/BGN');

// Returns "takhisti alopix vafis psimeni yi dhraskelizi iper nothrou kinos"
$slugger->transliterate('Τάχιστη αλώπηξ βαφής ψημένη γη, δρασκελίζει υπέρ νωθρού κυνός', 'Lower(); Any-Latin; Latin-ASCII; [^\x20\x41-\x5A\x61-\x7A] Remove');
```

## Api documentation

https://phpdoc.fenric.ru/

## Useful links

http://site.icu-project.org/<br>
http://userguide.icu-project.org/transforms/general<br>
http://demo.icu-project.org/icu-bin/translit