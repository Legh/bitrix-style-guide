Стандарты программирования для платформы 1С-Битрикс
=====================
В этом руководстве описаны рекомендуемые техники при разработке под платформу 1С-Битрикс (далее просто Битрикс).
Весь PHP код должен написан в соответствии со стандартом [PSR-1][]
Стиль написания кода должен соответствовать стандарту [PSR-2][]

[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md

1. Общие положения
-----------
Часть описанных в этом разделе требований уже указана в стандартах, приведенных выше, но отметим особенно важные.
- ОБЯЗАТЕЛЬНО должны использоваться только `<?php` и `<?=` теги. Тег `<?` использовать НЕЛЬЗЯ.
- ОБЯЗАТЕЛЬНО использование кодировки UTF-8 без BOM.

2. Базовые правила при разработке под Битрикс
-----------
- при добавлении кода в файл init.php РЕКОМЕНДУЕТСЯ выносить логически сгруппированный код в отдельные файлы и подключать их внутри init.php
- НЕ РЕКОМЕНДУЕТСЯ использовать цифровые значения в GetList, GetByID и схожих методах, которые принимают различные ID. РЕКОМЕНДУЕТСЯ создать файл со всеми необходимыми константами и вызывать их имена. У каждой константы ДОЛЖНО быть «говорящее» именование и комментарий.
Не правильно:
```php
    <?php
    $comments = CIBlockElement::GetList(Array(), Array("IBLOCK_ID" => 12));
```
Правильно:
* Создаем файл constants.php и указываем в нем:
```php
    <?php
    //ИБ с комментариями пользователей
    const COMMENTS_IBLOCK_ID = 12;
```
* Подключаем этот файл в ini.php
```php
    <?php
    //Константы проекта
    include_once($_SERVER["DOCUMENT_ROOT"] . '/bitrix/php_interface/includes/constants.php');
```
* Используем константу
```php
    <?php
    $comments = CIBlockElement::GetList(Array(), Array("IBLOCK_ID" => COMMENTS_IBLOCK_ID));
```