***************
camera
***************

Controls camera objects within a scene.

Overview
=========
.. csv-table::
    :header: Name, Description, Returns, Parameters
    :widths: 5, 15,5,10

    changeTo2D, Change scene mode to 2D, none, ``camera.changeTo2D()``
    changeTo3D, Change the Scene mode to 3D, none, ``camera.changeTo3D()``
    getEyePos,	Get positions of all camera, Vector3,	``camera.getEyePos()``
    getTargetPos,	Get the position of the fixation point of the camera(s),	Vector3,	``camera.getTargetPos()``
    fit,	Focus all cameras on specified object,	none,	``camera.fit(obj)``
    flyTo,	Move the camera to new position specified by the function,	none,	``camera.flyTo({json})``
    lookAt,	Set the Point of view of a camera,	none,	``camera.lookAt(pos)``
    setPosition,	Set the position of a camera, none,``camera.setPosition(pos)``
    stopFlying,	"Stops the camera at the position specified by the function. Often used with the function ``FlyTo``",	none,	``camera.stopFlying()``

|

camera.changeTo2D
====================

Change scene mode to 2D.

Parameters
^^^^^^^^^^
none

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   // Changes the scene mode to '2D'. 
   // If the current scene mode is already in 2D, the scene does not change
   camera.changeTo2D()


|

camera.changeTo3D
====================

Change scene mode to 3D.

Parameters
^^^^^^^^^^
none

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   // Changes the scene mode to '3D'.
   // If the current scene mode is already in 3D, the scene does not change
   camera.changeTo3D()



|

camera.getEyePos
====================

Get the current position of the camera.

Parameters
^^^^^^^^^^
none

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   // print the position of the camera
   print(camera.getEyePos());  

|

camera.getTargetPos
====================

Get the fixation point position of the camera

Parameters
^^^^^^^^^^
none

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   // print fixation point position of the camera
   print(camera.getTargetPos());  

|

camera.fit
====================

Focus camera on specified object

Parameters
^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    obj, "object referance, which will be focued by camera"
    

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   /** create box object and have the camera focus on the object. 
   The focus point is the center point of the object. 
   The position of the camera is based on size of the object */

   var object.create("AB052B5B646E4A48B9C045096FF9B088");
   camera.fit(obj);


|

camera.flyTo
=======================

Move the position and the fixation point of the camera within a certain time, then, execute a function.

Parameters
^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    *{json}*, "``json message``, including position, fixation point ,time, execute function"
    

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   /** move camera to position (2,3,4) and change the fixation point to (3,4,5 ) 
   within 2 seconds, then print “OK”.*/

   camera.flyTo({
    "eye":Vector3(2,3,4),
    "target":Vector3(3,4,5),
    "time":2.0,
    "complete":function(){print("OK!")}
    }) 

|

camera.lookAt
====================

Set camera's fixation point as given Vector

Parameters
^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    pos, "Vector3 variable; camera's fixation point"
    

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   // set camera's fixation point to be the center point of the object 'obj'.
   camera.lookAt(obj.center);

|

camera.setPosition
=======================

Set camera's position as given Vector

Parameters
^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    pos, "``Vector3`` camera's position"
    

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   // set camera's position to (0,1,2)
   camera.setPosition(Vector3(0,1,2));


|

camera.stopFlying
====================

Set camera's position as given Vector

Parameters
^^^^^^^^^^
none
    

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   // Create a button named'Execute'. 
   // Clicking on the button will stop moving the position or fixation point of the camera.
   
   camera.setPosition(Vector3(0,1,2));

   camera.flyTo({

    "eye":Vector3(2,3,4),

    "target":Vector3(3,4,5),

    "time":2.0,

    "complete":function(){print("OK!")}})

    gui.createButton("Execute", Rect(10, 50, 200, 50), function() {camera.stopFlying();})

    

