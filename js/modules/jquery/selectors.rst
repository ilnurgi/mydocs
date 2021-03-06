.. _selector:

Селекторы
=========

Простые
-------

======================= ========
селектор                описание
======================= ========
$('*');                 все
$('#sidebar');          все, с id == sidebar
$('div.post');          все div, с class == post
$('.post');             все, с class == post
$('div');               все div
$('div, span');         все div и span
======================= ========


Комбинированные
---------------

======================= ========
селектор                описание
======================= ========
$('div span');          все span внутри div
$('div > span');        все span внутри div, span - прямой потомком div 
$('div + span');        все span после div
$('div ~ span');        все span смежные по отношению к div
======================= ========


Фильтры аттрибутов
------------------

=============================== ========
селектор                        описание
=============================== ========
$("div[title]");                значение атрибут title
$("div[title='title']");        значение атрибута равна title
$("div[title!='title']");       значение атрибута не равна 'title'
$("div[title^='ti']");          значение атрибута начинается с ti
$("div[title$='le']");          значение атрибута заканчивается на le
$("div[title*='itl']");         значение атрибута содержит "itl"
$("div[title~='itl']");         значение атрибута содержит "itl" как слово
$("div[title|='itl']");         зна­че­ние ат­ри­бу­та на­чи­на­ет­ся с itl и не­обя­за­тель­но­го де­фи­са
=============================== ========


Фильтры по типам элементов
--------------------------

======================= ========
селектор                описание
======================= ========
:button                 элементы типа button  
:checkbox               элементы типа checkbox
:file                   элементы типа file
:header                 элементы типа header
:image                  элементы типа image
:input                  элементы типа input
:password               элементы типа password
:radio                  элементы типа radio
:reset                  элементы типа reset
:submit                 элементы типа submit
:text                   текстовые элементы
======================= ========


Фильтры по состоянию элементов
------------------------------

======================= ========
селектор                описание
======================= ========
:animated               все анимируемые в данный момент элементы
:checked   
:disabled   
:enabled    
:hidden                 скрытые элементы
:selected               выбранные элементы
:visible
======================= ========


Фильтры по позиции
------------------

======================= ========
селектор                описание
======================= ========
:eq(n)                  элемент с указанным индексом
:even                   все четные элементы
:first                  первый из подходящих
:gt(n)                  элементы, индекс которых превышает указанный
:last                   последний из подходящих
:lt(n)                  элменеты, индекс которых меньше указанной
:nth(n)
:odd                    все нечетные
======================= ========


Фильтры по позиции в документе
------------------------------

======================= ========
селектор                описание
======================= ========
:first-child     
:last-child      
:only-child      
:nth-child(n)
:nth-child(even)
:nth-child(odd)
:nth-child(xn+y)                 
======================= ========


Фильтры прочие
--------------

======================= ========
селектор                описание
======================= ========
:contains(text)         элементы, содержащие текст
:empty           
:has(selector)          элементы, которые содержат хотябы один элемент, соответсвующий указанному 
:not(selector)
:parent                 элементы являются родительским по отношению к другим элементам
======================= ========


.. code-block:: js

    // div с атрибутом title == "title", видимый, содержащий теги p
    $("div[title = 'title']:visible:has(p)");
    
    // выбранные элементы select
    $("form select option:selected");
    
    // получение выбранного значения радиобатона с именем some
    $("form :radio[name=some]:checked").val();

    // выбор всех выбранных чекбоксов
    $("form :checkbox:checked");