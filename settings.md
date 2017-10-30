# Параметры

## Общие параметры. Минимальные

* версия веб-сервера: Apache 2.2;
* версия PHP 5.4 и выше;
* версия ядра Битрикс 14 и выше.
* **версия PHP 5.3 категорически не допускается (снята с поддержки, обновления безопасности не выпускаются)**;
* Режим работы php - модуль apache (mod_php);
* включена обработка .htaccess (mod_rewrite);
* время пинга от потенциального пользователя до сервера - менее 150мс;

## Общие параметры. Рекомендованные

Все что в минимальных, плюс:

* версия PHP 5.6 и выше
* версия ядра Битрикс 16 и выше
* включенный акселератор opcache
* время пинга от потенциального пользователя до сервера - менее 100мс
* доступ к аккаунту хостинга по ssh/sftp
* оценка производительности конфигурации по тестированию Битрикс (версии 15) - не ниже 20

## Установки PHP. Минимальные

```ini
default_charset = UTF-8
mbstring.func_overload = 2
mbstring.internal_encoding = UTF-8
memory_limit = 128M
realpath_cache_size = 4096k ; и больше
safe_mode = Off
short_open_tag = On
```

### Использование opcache

```ini
opcache.revalidate_freq = 0
opcache.validate_timestamps = 1
```

## Установки PHP. Рекомендованные

* доступная память (memory_limit)
  * для визитки, каталога - не менее 128 Mb
  * для магазина - не менее 256 Mb
* позволить загрузку файлов (file_uploads)
* показывать ошибки (display_errors)

## Требуемые модули PHP

* Multibyte String (mbstring)
* MySQL (mysql/mysqli)
* поддержка регулярных выражений (Perl-Compatible)

## Рекомендуемые модули PHP

* [Free Type Library](http://php.net/manual/ru/image.installation.php)
* [MCrypt](http://php.net/manual/ru/book.mcrypt.php)
* [Zlib Compression](http://php.net/manual/ru/book.zlib.php)
* [Библиотека GD](http://php.net/manual/ru/book.image.php) (функции для работы с графикой)
