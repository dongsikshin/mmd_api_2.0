***************
input
***************

Overview
=========

Inputs from keyboards and mouses.

.. csv-table::
    :header: Name, Description, Returns, Parameters
    :widths: 5, 15,5,10

    getKey,Get statue of holding down appointed ke,boolen,``getKey(keyCode)``
    getKeyDown,Get statue of pressing appointed key,boolen,``getKeyDown(keyCode)``
    getKeyUp,Get statue of releasing appointed key,boolen,``getKeyUp(keyCode)``
    getMouseButton,Get statue of pressing a mouse button,boolen,``getMouseButton(MouseCode)``
    getMouseButtonDown,Get statue of pressing a mouse button,boolen,``getMouseButtonDown(MouseCode)``
    getMouseButtonUp,Get statue of releasing the mouse button,boolen,``getMouseButtonUp(MouseCode)``

|


input.getKey
=======================

Check if user press and holds specific key.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    keyCode, "``KeyCode`` raw key code for keyboard events."


Example
^^^^^^^^^^
.. _getKey: 

.. code-block:: javascript
   :linenos:

    Player = { 
        obj : null,      
        function Update() {
                 //if user holds down key A, rotate obj -5 degree around its Y axis
                if (input.getKey(KeyCode.A))  this.obj.yaw(-5);

                //if user holds down key D, rotate obj 5 degree around its Y axis 
                if (input.getKey(KeyCode.D))  this.obj.yaw(5);

                //if user holds down key R, move obj to Vector3(3,0,3) in 2 seconds
                if (input.getKeyDown(KeyCode.R))  this.obj.moveTo(Vector3(3,0,3),2);


                //if user holds down key R, move obj to Vector3(-3,0,-3) in 2 second
                if (input.getKeyUp(KeyCode.R))  this.obj.moveTo(Vector3(-3,0,-3),2); 


                //if user clicks the left mouse button, print ' Pressed left click'
                if (input.getMouseButtonDown(0)) print("Pressed left click ");

                //if user clicks the right mouse button,print'Pressed right click'
                if (input.getMouseButtonDown(1)) print("Pressed right click "); 
            }
        }

    var obj = object.create("0bcba8ca78734b64a3dae3eb699a913c");

    var script = obj.addScript(Player);

    script.obj = obj;

    camera.enableMove = false;input.getKeyDown(keyCode);


|

input.getKeyDown
=======================

Check if user press specific key.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    keyCode, "``KeyCode`` raw key code for keyboard events."


Example
^^^^^^^^^^

See `getKey`_ 

|

input.getKeyUp
=======================

Check if user release specific key.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    keyCode, "``KeyCode`` raw key code for keyboard events."


Example
^^^^^^^^^^

See `getKey`_ 

|

input.getMouseButton
=======================

Check if user click and hold mouse button.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    MouseCode, "``int`` raw key code for mouse events."


Example
^^^^^^^^^^

See `getKey`_ 

|

input.getMouseButtonDown
=========================

Check if user click mouse button.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    MouseCode, "``int`` raw key code for mouse events."


Example
^^^^^^^^^^

See `getKey`_ 

|

input.getMouseButtonUp
=======================

Check if user release mouse button.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    MouseCode, "``int`` raw key code for mouse events."


Example
^^^^^^^^^^

See `getKey`_ 



