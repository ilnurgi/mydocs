.. py:module:: inspect

inspect - сбор информации о существующих объектах
=================================================

.. py:method:: cleandoc(doc)

    Приводит в порядок строку документирования doc, замещая все символы табуляции пробелами и удаляя отступы, которые могли быть добавлены, чтобы выровнять строку документирования в соответствии с другими инструкциями в функции или в методе.

.. py:method:: currentframe()

    Возвращает объект кадра стека, соответствующий кадру стека вызывающей функции.

.. py:method:: formatargspec(args [, varags [, varkw [, defaults]]])
    
    Возвращает отформатированную строку, представляющую значения, возвращаемые функцией :py:meth:`getargspec()`.

.. py:method:: formatargvalues(args [, varargs [, varkw [, locals]]])

    Возвращает отформатированную строку, представляющую значения, возвращаемые функцией :py:meth:`getargvalues()`.

.. py:method:: getargspec(func)

    Для заданной функции func возвращает именованный кортеж ArgSpec(args, varargs, varkw, defaults), где 

    * args – это список имен аргументов функции func, 
    * varargs – имя аргумента, начинающегося с символа * (если имеется),
    * varkw – имя аргумента, начинающегося с символов ** (если имеется), 
    * defaults – кортеж значений по умолчанию для аргументов или None, если аргументы со значениями по умолчанию отсутствуют. 

    Если в функции func имеются аргументы со значениями по умолчанию, кортеж defaults пред- ставляет значения последних n аргументов в списке args, где n – результат вызова функции len(defaults).

.. py:method:: getargvalues(frame)

    Возвращает значения аргументов, переданных функции с кадром стека frame. Возвращает кортеж ArgInfo(args, varargs, varkw, locals), где 

    * args - список имен аргументов, 
    * varargs – имя аргумента, начинающегося с символа * (если имеется), 
    * varkw – имя аргумента, начинающегося с символов ** (если имеется), 
    * locals – локальный словарь кадра стека.

.. py:method:: getclasstree(classes [, unique])
    
    Получая список classes связанных классов, эта функция воссоздает иерархию их наследования. Иерархия представлена как коллекция вложенных списков, где каждый элемент списка является списком классов, наследующих класс, непосредственно предшествующий этому списку. Каждый элемент вложенного списка является кортежем из 2 элементов (cls, bases), где cls – объект класса, а bases – кортеж базовых классов. Если в аргументе unique передается значение True, каждый класс будет включаться в возвращаемый список только один раз. В противном случае, когда используется множественное наследование, класс может появляться в списке несколько раз.

.. py:method:: getcomments(object)

    Возвращает строку, содержащую комментарии, непосредственно предшествующие объявлению объекта object в исходном программном коде наязыке Python. Если объект является модулем, возвращаются комментарии, расположенные в начале модуля. В случае отсутствия комментариев возвращается None.

.. py:method:: getdoc(object)

    Возвращает строку документирования объекта object. Перед этим строка документирования обрабатывается функцией cleandoc().

.. py:method:: getfile(object)

    Возвращает имя файла, в котором находится определение объекта object. Может вернуть TypeError, если эта информация не имеет смысла или недоступна (например, для встроенных функций).

.. py:method:: getframeinfo(frame [, context])

    Возвращает именованный кортеж Traceback(filename, lineno, function, code_context, index), содержащий сведения об объекте frame с информацией о кадре стека. Поля filename и lineno определяют местоположение в исходном программном коде. Аргумент context определяет количество строк конекста, которые будут извлекаться из исходного программного кода. Поле code_context в возвращаемом кортеже содержит список строк, составляющих контекст. Поле index – числовой индекс строки в этом списке, соответствующей кадру стека.

.. py:method:: getinnerframes(traceback [, context])

    Возвращает список записей в кадре стека для кадра объекта traceback с трассировочной информацией и для всех вложенных кадров. Каждая запись является кортежем из 6 элементов (frame, filename, lineno, funcname, code_context, index). Поля filename, lineno, context, code_context и index имеют тот же смысл, что и в кортеже, возвращаемом функцией getframeinfo().

.. py:method:: getmembers(object [, predicate])
    
    Возвращает все атрибуты объекта object. Обычно атрибуты выбираются с помощью атрибута __dict__ объекта, но эта функция может возвращать атрибуты, хранящиеся в других местах (например, строку документирования – из атрибута __doc__, имя объекта – из атрибута __name__ и так далее). Атрибуты возвращаются в виде списка пар (name, value). В необязательном аргументе predicate можно передать функцию, которая принимает атрибут объекта в качестве аргумента и возвращает True или False. В этом случае в список будут включены только те атрибуты, для которых функция predicate вернет True. В качестве функции predicate можно использовать такие функции, как isfunction() и isclass().

.. py:method:: getmodule(object)
    
    Возвращает модуль, в котором был объявлен объект object (если это возможно).

.. py:method:: getmoduleinfo(path)

    Возвращает информацию о том, как Python интерпретирует путь к файлу path. Если path не является модулем Python, возвращается None. В противном случае возвращается именованный кортеж ModuleInfo(name, suffix, mode, module_type), где name – это имя модуля, suffix – расширение имени файла, mode – режим открытия файла модуля и module_type – целочисленный код, определяющий тип модуля. Коды типов модулей определены в модуле imp.

.. py:method:: getmodulename(path)

    Возвращает имя модуля, заданного путем path. Если аргумент path не выглядит как модуль Python, возвращается None.

.. py:method:: getmro(cls)

    Возвращает кортеж классов, который является представлением порядка поиска методов в классе cls. Дополнительные подробности приводятся в главе 7 «Классы и объектно-ориентированное программирование».

.. py:method:: getouterframes(frame [, context])
    
    Возвращает список записей из текущего кадра стека и всех объемлющих кадров. Этот список является представлением последовательности вызовов функций, где первый элемент содержит информацию о кадре стека. Каждая запись является кортежем из 6 элементов (frame, filename, lineno, funcname, code_context, index), поля которого имеют тот же смысл, что и в кортеже, возвращаемом функцией getinnerframes(). Аргумент context имеет то же назначение, что и в функции :py:meth:`getframeinfo()`.

.. py:method:: getsourcefile(object)
    
    Возвращает имя файла с исходным программным кодом на языке Python, где находится определение объекта object.

.. py:method:: getsourcelines(object)

    Возвращает кортеж (sourcelines, firstline), соответствующий определению объекта object. Поле sourcelines – список строк с исходным программным кодом, а поле firstline – номер первой строки с исходным программным кодом. Если исходный код невозможно получить, возбуждает исключение IOError.

.. py:method:: getsource(object)
    
    Возвращает исходный программный код объекта object в виде единственной строки. Если исходный код невозможно получить, возбуждает исключение IOError.

.. py:method:: isabstract(object)
    
    Возвращает True, если объект object является абстрактным базовым классом.

.. py:method:: isbuiltin(object)

    Возвращает True, если объект object является встроенной функцией.

.. py:method:: isclass(object)
    
    Возвращает True, если объект object является классом.

.. py:method:: iscode(object)

    Возвращает True, если объект object является объектом с программным кодом.

.. py:method:: isdatadescriptor(object)

    Возвращает True, если объект object является дескриптором данных. Таковыми считаются объекты, определяющие оба метода: __get__() и __set__().

.. py:method:: isframe(object)

    Возвращает True, если объект object является кадром стека.

.. py:method:: isfunction(object)

    Возвращает True, если объект object является функцией.

.. py:method:: isgenerator(object)
    
    Возвращает True, если объект object является генератором.

.. py:method:: isgeneratorfunction(object)

    Возвращает True, если объект object является функцией-генератором. Отличие от функции isgenerator() состоит в том, что данная функция проверяет, является ли объект функцией, которая при вызове создает генератор. Не может использоваться для проверки, является ли генератор активным.

.. py:method:: ismethod(object)
    
    Возвращает True, если объект object является методом.

.. py:method:: ismethoddescriptor(object)
    
    Возвращает True, если объект object является дескриптором метода. Таковыми считаются объекты, не являющиеся методами класса и определяющие метод __get__(), но не определяющие метод __set__().

.. py:method:: ismodule(object)
    
    Возвращает True, если объект object является модулем.

.. py:method:: isroutine(object)
    
    Возвращает True, если объект object является пользовательской или встроенной функцией или методом.

.. py:method:: istraceback(object)
    
    Возвращает True, если объект object является объектом с трассировочной информацией.

.. py:method:: stack([context])

    Возвращает список записей, соответствующих текущему кадру стека. Каждая запись является кортежем из 6 элементов (frame, filename, lineno, funcname, code_context, index), содержащих ту же информацию, которая возвращается функцией getinnerframes(). Аргумент context определяет количество строк контекста, которые должны возвращаться для каждой записи кадра.

.. py:method:: trace([context])

    Возвращает список записей для кадров стека между текущим кадром и кадром, в котором возникло исключение. Первая запись соответствует текущей функции, а последняя – кадру, в котором возникло исключение. Аргумент context определяет количество строк контекста, которые должны возвращаться для каждой записи кадра.