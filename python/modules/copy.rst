.. title:: python copy

.. meta::
    :description: python copy
    :keywords: python copy

.. py:module:: copy

copy
====

модуль для копирования объектов 


.. py:method:: copy(obj)

    поверхностное копирование объекта


.. py:method:: deepcopy(obj [,visit])
    
    :param dict visit: используется для запоминания посещенных объектов, чтобы избежать зацикливания при копировании рекурсивных структур данных
    
    более глубокое копирование объекта