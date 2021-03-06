Строки, символы
===============

char
----

Строка фиксированный длины, дополненная пробелами

char(n)


varchar
-------

Строка с ограничем максимальной длины

varchar(n)


text, varchar
-------------

Строка без ограничения длины


Функции, выделение частей
-------------------------

length, char_length
+++++++++++++++++++

Длина строки в символах

.. code-block:: sql

    select
      length('Привет, мир!')
      , char_length('Привет, мир!')

    /*
        12
        12
    */

octet_length
++++++++++++

Длина строки в байтах, зависит от кодировки

.. code-block:: sql

    select
      octet_length('Привет, мир!')

    /*
        21
    */

position, strpos
++++++++++++++++

Позиция подстроки

.. code-block:: sql

    select
      position('мир' in 'Привет, мир!')
      , strpos('Привет, мир!', 'мир')

    /*
        9
    */

substring, substr
+++++++++++++++++

Выделение подстроки

.. code-block:: sql

    select
      substring('Привет, мир!' from 9 for 3)
      , substring('Привет, мир!' from 9)
      , substr('Привет, мир!', 9, 3)
      , substr('Привет, мир!', 9)

    /*
        мир
        , мир
        , мир!
        , мир!
    */

left, right
+++++++++++

Подстрока слева или справа

.. code-block:: sql

    select
      left('Привет, мир!', 6)
      , right('Привет, мир!', 4)

    /*
        Привет
        , мир!
    */

Функции, изменений
------------------

overlay
+++++++

Замена подстроки

.. code-block:: sql

    select
      overlay('Привет, мир!' placing 'PostgreSQL' from 9 for 3)

    /*
        Привет, PostgreSQL!
    */

replace
+++++++

Замена всех вхождений подстроки

.. code-block:: sql

    select
      replace('Привет, мир!', 'р', 'ррр')

    /*
        Пррривет, миррр!
    */

translate
+++++++++

Замена символов по соответствию

.. code-block:: sql

    select
      translate('Привет, мир!', 'Првтмие', 'Prvtm')

    /*
        Prvt, mr!
    */

lower, upper, initcap
+++++++++++++++++++++

Преобразование регистра (зависит от CTYPE)

.. code-block:: sql

    select
      lower('Привет, мир!')
      , upper('Привет, мир!')
      , initcap('Привет, мир!')

    /*
        привет, мир!
        ПРИВЕТ, МИР!
        Привет, Мир!
    */

trim, ltrim, rtrim, btrim
+++++++++++++++++++++++++

Отрезание символов с концов строки (по умолчанию — пробелы)

.. code-block:: sql

    select
      trim( leading 'Пр!' from 'Привет, мир!')
      , ltrim('Привет, мир!', 'Пр!')
      , trim(trailing 'Пр!' from 'Привет, мир!')
      , rtrim('Привет, мир!', 'Пр!')
      , trim( both 'Пр!' from 'Привет, мир!')
      , btrim('Привет, мир!', 'Пр!')

    /*
        ивет, мир!
        , ивет, мир!
        , Привет, ми
        , Привет, ми
        , ивет, ми
        , ивет, ми
    */

lpad, rpad
++++++++++

Дополнение слева или справа (по умолчанию — пробелами)

.. code-block:: sql

    select
      lpad('Привет, мир!', 17, '. ')
      , rpad('Привет, мир!', 17, '. ')

    /*
        . . .Привет, мир!
        , Привет, мир!. . .
    */

reverse
+++++++

переворачивает строку

.. code-block:: sql

    select
      reverse('Привет, мир!')

    /*
        !рим ,тевирП
    */

Функции, конструрирования
-------------------------

concat, concat_ws
+++++++++++++++++

Склейка строк (произвольное число аргументов)

.. code-block:: sql

    select
      concat('Привет,', ' ', 'мир!')
      , 'Привет,' || ' ' || 'мир!'
      , concat_ws(', ', 'Привет', 'о', 'мир!')

    /*
        Привет, мир!
        , Привет, мир!
        , Привет, о, мир!
    */

string_agg
+++

Агрегация строк

.. code-block:: sql

    select
      string_agg(s, ', ' order by id)
    from (
      values
        (2,'мир!'),
        (1,'Привет')
    ) v(id,s)

    /*
        Привет, мир!
    */

repeat
+++

Повторение строки

.. code-block:: sql

    select
      repeat('Привет', 2)

    /*
        ПриветПривет
    */

chr
+++

Символ по коду (зависит от кодировки)

.. code-block:: sql

    select
      chr(34)

    /*
        "
    */

Функции, экранирования
----------------------

quote_ident
+++++++++++

Представление строки в виде идентификатора

.. code-block:: sql

    select
      quote_ident('id')
      , quote_ident('foo bar')

quote_literal, quote_nullable
+++++++++++++++++++++++++++++

Ппредставление в виде строкового литерала

.. code-block:: psql

    SELECT
      quote_literal('id')
      , quote_nullable('id')
      , quote_literal($$What's up?$$)
      , quote_nullable($$What's up?$$)
      , quote_literal(null)
      , quote_nullable(null)

    /*
        'id'
        , 'id'
        , 'What''s up?'
        , 'What''s up?'
        , null
        , null
    */

format
++++++

Форматированный текст

.. code-block:: psql

    select
      format('Привет, %s!', 'мир')
      , format('UPDATE %I SET s = %L', 'tbl', $$What's up?$$)
      , 'UPDATE '||quote_ident('tbl')||' SET s = '||quote_nullable($$What's up?$$)

    /*
        Привет, мир!
        , UPDATE tbl SET s = 'What''s up?'
        , UPDATE tbl SET s = 'What''s up?'
    */

Функции, привидения типов
-------------------------

to_char
+++++++

Число, дату к строке

Форматирование строк

* 9 цифра
* 0 цифра с ведущим нулем
* . - (точка) - десятичная точка
* , - (разделитель) разделитель разрядов
* G - разделитель разрядов (из локали)
* D - точка или запятая (из локали)
* RN - римскими цифрами
* EEEE - экспоненциальная запись
* MI - минус (<0)
* PL - плюс (>0)
* SG - плюс или минус
* FM - без ведущих нулей и пробелов

Форматирование дат

* YYYY - год
* MM - месяц (01-12)
* MON - месяц (сокр.)
* MONTH - месяц полностью
* DD - день (01-31)
* D - номер дня недели (1-7)
* DY - день недели (сокр.)
* DAY - день недели
* HH - час (01-12)
* HH24 - час (00-23)
* MI - минуты
* SS - секунды
* TZ - часовой пояс
* OF - смещение часового пояса
* FM - без ведущих пробелов
* TM - перевод для дней и месяцев

.. code-block:: sql

    select
      to_char(3.1416, 'FM99D00')
      , to_char(3.1416, 'FM99D000000')
      , to_char(56789, '999G999G999')
      , to_char(123456789, '999G999G999')
      , to_char(123456789, '999G999G999')

    /*
        3,14
        3,141600
        56 789
        123 456 789
        123 456 789
    */

.. code-block:: sql

    select
      to_char(now(), 'DD.MM.YYYY HH24:MI:SSOF')
      , to_char(now(), 'FMDD TMmonth YYYY, day')

    /*
        15.11.2016 11:52:08+03
        , 15 ноября 2016, среда
    */

Функции, сравнения
------------------

