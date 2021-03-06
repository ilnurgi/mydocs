selectable - выбираемый элемент
===============================

.. py:function:: selectable([methodName, option, value])
.. py:function:: selectable([methodName, param_obj])
.. py:function:: selectable([param_obj])

    .. code-block:: js
        
        $('#selectable').selectable({
        });


    * `methodName`

        * `destroy` - Полностью удаляет всю функциональность взаимодействия Selectable из базового элемента

        * `disable` - Временно отключает функциональность взаимодействия Selectable для базового элемента

        * `enable` - Включает ранее отключенную функциональность взаимодействия Selectable для базового элемента

        * `option` - Позволяет получить или изменить значение одного или нескольких па­раметров

        * `refresh` - Обновляет состояние взаимодействия Selectable. Это вариант ручной настройки, аналогичный использованию значения false для парамет­ра autoRefresh

    * `param_obj`

        * `autoRefresh` - Если значение этой опции равно true, то в начале каждой операции выбора осуще­ствляется пересчет размеров и положений каждого из выбираемых элементов. Зна­чение по умолчанию — true

        * `cancel` - Строка селектора jQuery, предотвращающего выбор соответствующих элементов

        * `create` - Происходит в момент применения взаимодействия Selectable к данному элементу

        * `delay` - Определяет время, в течение которого должно осуществляться перетаскивание элемен­та, прежде чем он переместится. Значение по умолчанию — о; оно означает отсутствие задержки

        * `disabled` - Если значение этой опции равно true, то функциональность взаимодействия для данного элемента первоначально отключена. Значение по умолчанию — false

        * `distance` - Определяет расстояние, на которое пользователь должен перетащить элемент из его начальной позиции, прежде чем он действительно переместится. Значение по умолча­нию — 1 пиксель

        * `filter` - Селектор, используемый для выбора элементов в контейнере, наделенных функцио­нальностью взаимодействия Selectable. Значение по умолчанию — \*; ему соответ­ствуют все элементы

        * `selected` - Происходит по завершении выбора элемента. Если выбрано несколько элементов, то это событие наступает для каждого из них по отдельности

        * `selecting` - Происходит в момент начала выбора (путем нажатия кнопки мыши или перемещения указателя мыши)

        * `unselected` - Происходит при отмене выбора элемента. Если выбор отменен для нескольких элемен­тов, это событие наступает для каждого из них по отдельности

        * `unselecting` - Происходит в момент начала отмены выбора путем нажатия кнопки мыши