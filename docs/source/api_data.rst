***************
Data Interface
***************

Summary
=========

Momoda data infterface connect Momoda to third party systems, it can be used to scene initialization, push alarm, control objects, such as create, move, transform, remove, etc., in realtime.

There are three catelogies in Momoda data infterface, namely:

- I Interface
- M Interface
- R Interface

|

I Interface
============

I (short for Initialize) interface is used for scene initialization. Data push through *I Interface* will loaded by Momoda client automatically.

Usage
^^^^^^
.. csv-table::
    :widths: 5, 20

    url, "http://*{Your Momoda Server IP}*:8080/goods/save"
    http method, GET or POST
    parameters, "
                - ``g.sid``: scene ID
                - ``g.oid``: object ID
                - ``g.props``: object initialization data
                "

HTTP GET 
^^^^^^^^^^^^^^^^^

- request

.. code-block:: text
   :linenos:

        http://127.0.0.1:8080/goods/save?g.sid=20170320095733039126770&g.oid=cabinet1&g.props={"Initialized Data":"Initialized Data"}

.. note::

  request will push init data in JSON data {"Initialized Data":"Initialized Data"} to object ``cabinet1`` in scene ``20170320095733039126770``


- server response
  
  .. image:: images/data_resp_1.png
    :align: center
    :alt: response
    :width: 480

|

- sample request in html/javascript

.. code-block:: html
   :linenos:

    <!DOCTYPE html>

    <html>

    <head>

    <script src="jquery-1.11.1.min.js">

    </script>

    <script>

    $(document).ready(function(){

    $("button").click(function(){

    $.get('http://127.0.0.1:8080/goods/save?g.sid=20170320095733039126770&g.oid=cabinet1&g.props={"Initialized Data":"Initialized Data"}',

        function(data) { alert("Data:" + data);}

            );

    });

    });

    </script>

    </head>

    <body>

    <button>Submit data</button>

    </body>

    </html>


HTTP POST 
^^^^^^^^^^^^^^^^^

- request
    - url, ``http://*{Your Momoda Server IP}*:8080/goods/save``
    - POST message:

    .. code-block:: javascript
        :linenos:

        {

                g.sid:20170320095733039126770

                g.oid:cabinet1

                g.props:{"Initialized Data":"Initialized Data"}

        }

        request will push init data in JSON format {"Initialized Data":"Initialized Data"} to object ``cabinet1`` in scene ``20170320095733039126770``

|

- server response
  
  .. image:: images/data_resp_2.png
    :align: center
    :alt: response
    :width: 480


- sample request in html/javascript

.. code-block:: html
   :linenos:

    <!DOCTYPE html>

    <html>

    <head>

    <script src="jquery-1.11.1.min.js">

    </script>

    <script>

    $(document).ready(function(){

    $("button").click(function(){

        $.post("http://127.0.0.1:8080/goods/save",

        {

        "g.sid":"20170320095733039126770",

        "g.oid":"cabinet1",

        "g.props":'{"Initialized Data":"Initialized Data"}'    },

        function(data) { alert("Data:" + data);}

            );

    });

    });

    </script>

    </head>

    <body>

    <button>Submit data</button>

    </body>

    </html>



|

M Interface
============

use the'M interface'to push *realtime* data to the scene, typical user case could be showing *realtime* information upon sensor objects. For instance, shows realtime alarms of fire/gas sensor,  realtime location of cargo, current reading of temperature, etc.

.. warning::

    Data pushed to M Interface is stored in Momoda server's message queue, and there are no *message replay* for the queue, so if a Momoda client is  **newly connected** to server, it only shows the **current** message/data in queue.
  

Usage
^^^^^^
.. csv-table::
    :widths: 5, 20

    url, "http://*{Your Momoda Server IP}*:8080/data/putdata"
    http method, GET or POST
    parameters, "{JSON Message}"

HTTP GET 
^^^^^^^^^^^^^^^^^

- request

.. code-block:: text
   :linenos:

   http://127.0.0.1:8080/data/putdata?param={"20170320095733039126770":{"cabinet1": {"monitoring data":"monitoring data"}}}  

.. note::

  request will push init data in JSON data {"monitoring data":"monitoring data"} to object ``cabinet1`` in scene ``20170320095733039126770``


- server response
  
  .. image:: images/data_resp_3.png
    :align: center
    :alt: response
    :width: 480

- sample request in html/javascript

.. code-block:: text
   :linenos:


    <!DOCTYPE html>

    <html>

    <head>

    <script src="jquery-1.11.1.min.js">

    </script>

    <script>

    $(document).ready(function(){

    $("button").click(function(){

        $.get('http://127.0.0.1:8080/data/putdata?param={"20170320095733039126770":{"cabinet1": {"monitoring data":"monitoring data"}}}',

        function(data) { alert("Data:" + data);}

            );

    });

    });

    </script>

    </head>

    <body>

    <button>Submit data</button>

    </body>

    </html>

HTTP POST 
^^^^^^^^^^^^^^^^^

- request
    - url, ``http://*{Your Momoda Server IP}*:8080/data/putdata``
    - POST message:

    .. code-block:: javascript
        :linenos:

        {

            param:{"20170320095733039126770":{"cabinet1":{"monitoring data":"monitoring data"}
        }

.. note::

    request will push init data in JSON format {"monitoring data":"monitoring data"}  to object ``cabinet1`` in scene ``20170320095733039126770``

|

- sample request
  
  .. image:: images/data_resp_4.png
    :align: center
    :alt: response
    :width: 480

|

- sample request in html/javascript

.. code-block:: html
    :linenos:

    <!DOCTYPE html>

    <html>

    <head>

    <script src="jquery-1.11.1.min.js">

    </script>

    <script>

    $(document).ready(function(){

    $("button").click(function(){

        $.post("http://127.0.0.1:8080/data/putdata",

        {

    param:'{"20170320095733039126770":{"cabinet1":{"monitoring data":"monitoring data"}}}'    },

        function(data) { alert("Data:" + data);}

            );

    });

    });

    </script>

    </head>

    <body>

    <button>Submit data</button>

    </body>

    </html>

|

R Interface
============

Remove any initialization data in a scene.

Usage
^^^^^^
.. csv-table::
    :widths: 5, 20

    url, "http://*{Your Momoda Server IP}*:8080/goods/remove"
    http method, GET
    parameters, "
                - ``sid`` scene ID "

HTTP GET 
^^^^^^^^^^^^^^^^^

- request

.. code-block:: text
   :linenos:

   http://127.0.0.1:8080/goods/remove?sid=20170320095733039126770&oid=cabinet1

.. note::

  request will remove all initialization data from object ``cabinet1`` in scene ``20170320095733039126770``

|

- server response
  
  .. image:: images/data_resp_5.png
    :align: center
    :alt: response
    :width: 480

|

- sample request in html/javascript

.. code-block:: text
   :linenos:

    <!DOCTYPE html>

    <html>

    <head>

    <script src="jquery-1.11.1.min.js">

    </script>

    <script>

    $(document).ready(function(){

    $("button").click(function(){

        $.get('http://127.0.0.1:8080/goods/remove?sid=20170320095733039126770&oid=cabinet1',

        function(data) { alert("Data:" + data);}

            );

    });

    });

    </script>

    </head>

    <body>

    <button>Submit data</button>

    </body>

    </html>

|

