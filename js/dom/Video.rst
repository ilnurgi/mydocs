Video - HTML video
==================


.. py:class:: Video()

    Наследник :py:class:`MediaElement`


    .. py:attribute:: audio
        
        Это свой­ст­во оп­ре­де­ля­ет ау­дио­па­ра­мет­ры ви­део­за­пи­си. Па­ра­мет­ры ука­зы­ва­ют­ся в HTML-ат­ри­бу­те audio в ви­де спи­ска на­зва­ний па­ра­мет­ров, раз­де­лен­ных про­бе­ла­ми, и  в  про­грамм­ном ко­де на язы­ке Ja­va­Script от­ра­жа­ют­ся в  мно­же­ст­во DOMSet­table­TokenList. 


    .. py:attribute:: height
        
        Вы­со­та эле­мен­та <video> на эк­ра­не в CSS-пик­се­лах. Со­от­вет­ст­ву­ет HTML-ат­ри­бу­ту height.


    .. py:attribute:: poster
        
        URL-ад­рес изо­бра­же­ния, ото­бра­жае­мо­го в  ка­че­ст­ве «афи­ши» до то­го, как бу­дет за­пу­ще­но про­иг­ры­ва­ние ви­део­за­пи­си. Со­от­вет­ст­ву­ет HTML-ат­ри­бу­ту poster.

    .. py:attribute:: videoHeight
    .. py:attribute:: videoWidth
        
        Эти свой­ст­ва воз­вра­ща­ют ис­тин­ную вы­со­ту и ши­ри­ну кад­ра ви­део­за­пи­си в CSS-пик­се­лах. Эти свой­ст­ва бу­дут иметь ну­ле­вые зна­че­ния, по­ка эле­мент <video> не за­гру­зит ме­та­дан­ные (по­ка свой­ст­во readyState име­ет зна­че­ние HAVE_NOTHING, и не бы­ло сге­не­ри­ро­ва­но со­бы­тие «loadedmetadata»).


    .. py:attribute:: width
        
        Же­лае­мая ши­ри­на эле­мен­та <video> на эк­ра­не в  CSS-пик­се­лах. Со­от­вет­ст­ву­ет HTML-ат­ри­бу­ту width.