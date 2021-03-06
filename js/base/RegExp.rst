.. title:: js regexp

.. meta::
    :description:
        Описание javascript объекта RegExp
    :keywords:
        js regexp

RegExp
======

.. code-block:: js

    /x[eaoy]n/
    //xen, xan, xon, xyn

    /[^b]log/
    //dlog, flog

    /[A-Z]/

====== =====================
символ обозначение
====== =====================
\      экранирование
.      любой символ
*      0 и более 
+      1 и более
?      0 или 1
\b     разделитель между словами
\d     цифра
\D     не цифра
\s     пробел
\w     буквы, цифры и _
\W     НЕ буквы, цифры и _
[A-Z]  символ из указанных
$      конец данных
^      начало данных
[^]    НЕ
|      ИЛИ
{m, n} от m до n повторений
()     запоминающие скобки
====== =====================

* g - глобальный поиск
* i - не различать строчные и прописные
* m - многострочный поиск


.. py:class:: RegExp(template, flags)

    Конструктор регулярных выражений

    Наследник :py:class:`Object`


    .. code-block:: js

        var a = new RegExp('\\w+c', 'igm');
        var re = /\w+c/igm


    .. py:attribute:: global

        Глобальный поиск


    .. py:attribute:: ignoreCase

        Не учитывать регистр


    .. py:attribute:: lastIndex

        Позиция символа при последнем обнаружении соответсвия


    .. py:attribute:: multiline

        Многострочный поиск


    .. py:attribute:: source

        Исходный текст регулярки


    .. py:method:: exec([string])

        Возвращает массив найденных элементов в строке

        .. code-block:: js

            var a = /\d/g;

            a.exec('kj5k3');
            // ['5']

            a.exec('kj5k3');
            // ['3']


    .. py:method:: test(string)

        Возвращает булево, есть ли совпадение

        .. code-block:: js

            var a = /\d/;

            a.test('qw');
            // false

            a.test('123');
            // true
