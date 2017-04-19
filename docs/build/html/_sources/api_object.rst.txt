*****************
object
*****************

Control the objects within the scene.


Overview
=========
.. csv-table::
    :header: Name, Description, Returns, Parameters
    :widths: auto

    create,	Create an object,Returns the object type of the created object,	"``object.create(bundleId,parentObj,callback,pos,scale)``"
    createArrowLine, "Create an arrow line", "Returns the object type of the created arrow line", "``object.createArrowLine(vertices,{json})``"
    createCurveLine,"Create a curved line", "Returns the object type of the curved line",	"``object.createCurveLine(vertices, bundleOrColorOrMat, parentObj, width, textiling, texOffSet)``"
    destroyAll,	Delete all the objects created by a script,none,``object.destroyAll()``
    find,"Find the object using uid", "Returns the object type of all exisiting objects", ``object.find(uid)``

|

object.create
==============

Create object.

Parameters
^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    bundleId, "``string`` , the id of the object"
    parentObj, "``BaseObject``,  parent of the object"
    callback, "``function``, Callback function. After loading the object, execute this callback"
    pos, "``Vector3`` ; the position of the object"
    scale, "``Vector3``; the size of the object"


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   /** Create object'obj1'and set its position to (1,0,1)
   Create a second object 'obj2'and set its parent to be obj1 and its position to (2,0,1)
   scale (1,2,3), after loading obj2, execute callback, rotate the obj1 45 degree of Y (this time obj1 is obj2's parent, 
   so obj1 and obj2 will rotate together.) */

   var obj1 = object.create("AB052B5B646E4A48B9C045096FF9B088",Vector3(1,0,1));
   var obj2 = object.create("AB052B5B646E4A48B9C045096FF9B088",obj1,function(){obj1.yaw(45)},Vector3(2,0,1),Vector3(1,2,3));


object.createArrowLine
=======================

Create arrowed line.

Parameters
^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    vertices, "``array``  or ``vector3List`` ; the set of points on the arrowed line"
    *{json}*, "json message; includes the color of the arrow and the color of the line."


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:
   
    //define a Vector array
    var vecArray2 = [Vector3(0, 1, 20), Vector3(10, 1, 20)];

    
    //Create an arrowed line. Set the start position to (0,1,20) and the end position to (10,1,20). 
    //The color of the line is set to red, the color of the arrow is set to green.

    object.createArrowLine(vecArray2, {

    "color": Color.red,

    "arrowColor": Color.green});


object.createCurveLine
=======================

Create curve line.

Parameters
^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    vertices, "``array`` or ``Vector3List``；The set of the points on the curve line"
    bundleOrColorOrMat, ``string``  or ``color`` 
    parentObj, ``BaseObject``; the parent of the curve line
    width, ``float``; the width of the curve line
    textiling, repeatability of the material
    texOffSet, the offset of the material


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:
   
    // create a curve line named curveLine1
    var vecList = Vector3List();

    vecList.Add(Vector3(0,1,0));

    vecList.Add(Vector3(10,1,0));

    vecList.Add(Vector3(10,1,5));

    var curveLine1=object.createCurveLine(vecList, Color.green);


    // Create a curve line named 'curveLine2'. Set the material of the curve line to specified material. 
    // Set the parent of'curveLine2'to'curveLine1'. 
    //Set the repeatability of'curveLine2's' material to (1,2) and the offset of it's material to (0,0)

    var vecArray = [Vector3(0,1,5), Vector3(0,2,15), Vector3(10,4,15), Vector3(10,6,5)];

    var curveLine2 = object.createCurveLine(vecArray, "1D2702801708453680664DCABE70890B",curveLine1,2,Vector2(1,2),Vector2(0,0))



|

object.destroyAll
=======================

Destoy all the objects created by a script

Parameters
^^^^^^^^^^^^

None

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    //create obj
    var obj  = object.create("AB052B5B646E4A48B9C045096FF9B088");


    //create curveLine
    var vecArray = [Vector3(0,1,5), Vector3(0,2,15), Vector3(10,4,15), Vector3(10,6,5)];

    var curveLine1=object.createCurveLine(vecArray, Color.green);


    //Create a button called 'Delete'. Clicking on the button'Delete'will destroy all objects created by this script.
    gui.createButton("Delete", Rect(100, 100, 100, 30), function() {object.destroyAll()})




    
    
object.find
=======================

Find object by object ID.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    uid, ``string`` object uid


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    // Find Object with an Uid equal to'Object01', 
    // then rotate this object around the Y-axis at a 45 degree angle.
    object.find("Object01");
    obj.yaw(-45);


   



   


