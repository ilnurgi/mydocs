Smart-grid
==========

Библиотека для построения сеток

.. code-block:: sh

    npm install smart-grid

.. code-block:: js

    // smartgrid.js
    const smartgrid = require('smart-grid');
    smartgrid();


col
---


col-float
---------


col-padding
-----------


offset
------


offset-left
-----------


offset-right
------------


offset-padding
--------------


offset-xs
---------


row-flex
--------


row-float
---------


size
----


wrapper
-------


.. code-block:: text

    .wrapper {
        .wrapper();
    }

    .items{
        .row-flex;
        justify-content: center;

        .item{
            .col();
            .size(6);
            .size-md(12);
            .size-xs(24);
            .offset(1);
        }
    }


.. code-block:: text

    .wrapper{
        .wrapper();
    }

    .items{
        .row-float;

        .item{
            .col();
            .col-float();
            .size(6);
            .size-sm(12);
        }
    }