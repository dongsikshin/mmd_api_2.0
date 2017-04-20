***************
BaseObject
***************

Overview
=========
Provides actions on object.

.. csv-table::
    :header: Name, Description, Returns, Parameters
    :widths: auto

    addGravity,Add a gravity value to a specified object,none,"``BaseObject.addGravity(mass)``"
    addScript,Add a script to a specified object,Returns the type of script added to the object,"``BaseObject.addScript(script, name)``"
    addTail,Add a tail to a specified object. Commonly used with the function movePath,none,"``BaseObject.addTail({json})``"
    clone,Copy an existing object,baseObject,"``BaseObject.clone()``"
    destroy,Remove an existing object,BaseObject,"``BaseObject.destroy()``"
    getPosition,Acquire the position of a specified object,Vector3,"``BaseObject.getPosition()``"
    getScale,Acquire the scale of a specified object,Vector3,"``BaseObject.getScale()``"
    movePath,Move object by a specified parameter,none,"``BaseObject.movePath({json})``"
    moveTo,Move object to a position within a given time,none,"``BaseObject.(pos,time)``"
    pitch,Angel of rotation(in degree) of the object around its pivot point along X axis,none,"``BaseObject.pitch(degree)``"
    playAnim,Play an animation,none,"``BaseObject.playAnim(animName)``"
    removeScript,Remove a script from the specified object,none,"``BaseObject.removeScript(name)``"
    roll,Angel of rotation (in degree) of the object around its pivot point along the Z axis,none,"``BaseObject.roll(degree)``"
    setAnimSpeed,Set the animation speed of a specified object,none,"``BaseObject.setAnimSpeed(speed)``"
    setColor,Set the color of a specified object,none,"``BaseObject.setColor(color)``"
    setColorFlash,"Set the flash state, flash color and flash time of a specified object",none,"``BaseObject.setColorFlash(enable, color,time)``"
    setPickEnabled,Set the selectable state of the specified object. Commonly used with the'Mouse event'functions,none,"``BaseObject.setPickEnabled(enable)``"
    setPosition,Set the object's position,none,"``BaseObject.setPosition(x,y,z)``"
    setPositionXZ,Set the object's horizontal position,none,"``BaseObject.setPositionXZ(x,z)``"
    setPositionY,Set the object's position along the Y axis,none,"``BaseObject.setPositionY(y)``"
    SetScale,Set the scale of the object,none,"``BaseObject.setScale(x,y,z)``"
    setTransparent,Set the transparency of a specified object,none,"``BaseObject.setTransparent(trans)``"
    stopAnim,Stop a specified object's animation,none,"``BaseObject.stopAnim()``"
    stopMoving,Stop the object moving,none,"``BaseObject.stopMoving()``"
    transformPoint,Change specified coordinates of object from relative coordinates to absolute coordinates,Vector3,"``BaseObject.transformPoint(pos)``"
    translate,Move a specified object in a specified direction and distance,Vector3,"``BaseObject.translate(pos)``"
    yaw,Angel of rotation (in degree) of the object around its pivot point along the Y axis,none,"``BaseObject.yaw(degree)``"

|

BaseObject.addGravity
=======================

Add gravitational value to a object

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: auto

    mass, ``float`` the weight of the object


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    //add gravity to a 3.5 KG weight object
    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
    obj.addGravity(3.5)

|

BaseObject.addScript
=======================

Add script to a object

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: auto

    script, ``script`` to associate with the object
    name, ``string`` name of the script


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    /** Create a script named'AutoRtate'used to define the speed of object'objOption'. 
    A script may include a'Start'and'Update' function which is automatically recognized by the system. 
    The'Start'function will be called only once while the'Update'function will be called on repeatedly */

   AutoRotate = {

    speed : 0,

    objOption : null,

    function Start() {this.speed = util.randomFloat(1, 8);}

    function Update() {this.objOption.yaw(this.speed); }
    
    }

    //create object
    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088", Vector3(2.5, 0, 0));

    //add script “rotation” to object
    var script = obj.addScript(AutoRtate,"rotation");

    //set script's attribute objOption to be object; now function Update can rotate obj by its Y axis in a random speed
    script.objOption = obj;

|


BaseObject.addTail
=======================

Add trail to a specified object. Most Commonly used with the function movePath. Often used to increase the visual effects of an object.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    *{json}*, "json format includes start width, end width ,end color and time"


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    //create object
    var obj =object.create("AB052B5B646E4A48B9C045096FF9B088");
    var path = Vector3List();

    //generate 36 vector3 point, add them to a Vector3List, this could be seen as a circle, its radius is 10
    for (var degree = 0; degree < 360; degree += 10)
    { 
        path.Add(Vec3(Math.Cos(degree*Math.Deg2Rad)*10,0.5,Math.Sin(degree*Math.Deg2Rad)*10));
    }

    // move an object along the path in 10 seconds repeatly, whilst moving, 
    // the object will always look at (0,0,0)，
    obj.movePath({

        "path": path,

        "time": 10,

        "lookPos": Vector3.zero,

        "loopType": "loop"

    }); 


    //add a tail, start width 0.6, end width 0, color is red, lasting 5 seconds
    obj.addTail({

    "startWidth": 0.6,

    "endWidth":0,

    "color":Color.red,

    "time": 5

    });

|

BaseObject.clone
=======================

Clone a object.

Parameters
^^^^^^^^^^^^

None.


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   //Create an object, copy it and name is'obj2'. Then rotate'obj2'along the Y-Axis at a 45 degree angle

   var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");

   var obj2=obj.clone();

   obj2.yaw(45)

|

BaseObject.destroy
=======================

Remove a object.

Parameters
^^^^^^^^^^^^

None.


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   //Create an object named 'Obj'. Create a button named'Delete'with the size (10,100,100,20). 
   //click on this button to remove object'obj'from the scene
   
   var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");

   gui.createButton("Delete",Rect(10,100,100,20),function(){obj.destroy()})

|

BaseObject.getPosition
=======================

Get position of a object.

Parameters
^^^^^^^^^^^^

None.


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   //Create an object and print its position
   
   var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
   print(obj.getPosition())

|

BaseObject.getScale
=======================

Get scale information of a object.

Parameters
^^^^^^^^^^^^

None.


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

   //Create an object and print its scale
   
   var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
   print(obj.getScale())

|

BaseObject.movePath
=======================

Move object along pre-defined path.

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    *{json}*, "json format, specify path, time, target point, if loop, etc."



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    //Create object
    var obj =  object.create("AB052B5B646E4A48B9C045096FF9B088");

    //Generate 36 Vector3 point, add them in a Vector3List, you could see this Vector3List as a circle

    var path = Vector3List();

    for (var degree = 0; degree < 360; degree += 10)

    path.Add(Vec3(Math.Cos(degree*Math.Deg2Rad)*10,0.5,Math.Sin(degree*Math.Deg2Rad)*10));

    
    //Move an object along a path in 10 seconds , whilst moving ,the object will always face the vector (0,0,0) , 
    //after the object completes the movement , loop this function

    obj.movePath({

    "path": path,

    "time": 10,

    "lookPos": Vector3.zero,

    "loopType": "loop"

    });

|

BaseObject.moveTo
=======================

Move object to target position within a certain time

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    pos, "``Vector3`` destination position"
    time, "``float`` moving time"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    // Create object, move it to (10,0,0) in 5 seconds
    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
    obj.moveTo(Vector3(10, 0, 0), 5.0)

|

BaseObject.pitch
=======================

Rotate object on the X-axis by degree

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    degree, "``float`` degree of rotation"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    //Create an object and rotate the object on the X-axis at a 45 degree angle.
    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
    obj.pitch(45)

|

BaseObject.playAnim
=======================

Play object's animation

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    animName, "``string``  name of the animation"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    // Create an object named'obj'. Create a button with size (100,100,100,30). 
    // Pressing on this button will execute the “Run” animation of the object.
    var obj = object.create("0bcba8ca78734b64a3dae3eb699a913c");
    gui.createButton("Run", Rect(100, 100, 100, 30), function() {obj.playAnim("Run");});

|


BaseObject.removeScript
=======================

Move script associate with object

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    name, "``string``  name of the script"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    AutoRtate = {

    speed : 0,

    objOption : null,

    function Start() {this.speed = util.randomFloat(1, 8);}

    function Update() {this.objOption.yaw(this.speed); }}

    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088", Vector3(2.5, 0, 0));

    var script = obj.addScript(AutoRtate,"rotation");

    script.objOption = obj;

    //Create a button. Pressing on this button will remove the “rotation” script from the object'obj'.

    gui.createButton("Remove Script", Rect(100, 100, 100, 30),function(){obj.removeScript("rotation")})

|

BaseObject.roll
=======================

Rotate object a specified degree around the Z-axis (clockwise)

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    degree, "``float`` degree of rotation"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    //Create an object and rotate the object on the X-axis at a 45 degree angle.
    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
    obj.roll(45)

|

BaseObject.setAnimSpeed
=======================

Set the animation speed of a specified object

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    speed, "``float`` speed of animation playing"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    

    var obj = object.create("0bcba8ca78734b64a3dae3eb699a913c");

    gui.createButton("Run", Rect(100, 100, 100, 30), function() {obj.playAnim("Run");});

    //Create a button. Pressing on this button will set the objects animation speed to'4.5'
    gui.createButton("Accelerate", Rect(100, 150, 100, 30), function() {obj.setAnimSpeed(4.5)})

|

BaseObject.setColor
=======================

Set object color

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    color, "``color``"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    
    //Set the object color to blue

    var obj = object.create("FF2A3E364B1E4B928891E05A9279C7A7", Vector3(0, 0, 0));

    obj.setColor(Color.blue);

|

BaseObject.setColorFlash
=========================

Set flash state, flash color and flash interval of a specified object

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    enable, "``boolen`` turn flash 'On' or' Off'"
    color, "``color`` flash color"
    time, "``float`` flash interval"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    
    // Create object and set flash to'On', flash color to 'Green' and Flash interval to 2.5 seconds.

    var obj = object.create("FF2A3E364B1E4B928891E05A9279C7A7", Vector3(4, 0, 0));

    obj.setColorFlash(true, Color.green,2.5);

|

BaseObject.setPickEnabled
=========================

Set selectable state of the specified object. Commonly use with the 'Mouse event' functions

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    enable, "``boolen`` turn pickable 'On' or' Off'"




Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");

    var dragObj = null;

    util.addEventListener("dragstart", function(event) {

    if (event.obj && event.button == 0) {

    dragObj = event.obj;

    dragObj.setPickEnabled(false)

    camera.enableRot = false; }});

    // Add a “dragstart” event to an object named'obj'. 
    // Left clicking and dragging object'obj'will change the selectable state to false (Prevents object from being repeatedly dragged).

    util.addEventListener("drag", function(event) {

    if (dragObj && event.button == 0)

    dragObj.pos = event.pos;});

    util.addEventListener("dragend", function(event) {

    if (dragObj && event.button == 0) {

    dragObj.setPickEnabled(true);

    dragObj = null;

    camera.enableRot = true;}});

|

BaseObject.setPosition
=========================

Set object position

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    x, "``float`` X-Axis value"
    y, "``float`` Y-Axis value"
    z, "``float`` Z-Axis value"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    
    //Set the object's position to (0,5,0)

    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");

    obj.setPosition(0, 5, 0);

|

BaseObject.setPositionXZ
=========================

Set object horizontal position

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    x, "``float`` X-Axis value"
    z, "``float`` Z-Axis value"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    
    // Set the object's horizontal position to (1,1)

    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");

    obj.setPositionXZ(1,1);

    
|


BaseObject.setPositionY
=========================

Set object Y-Axis coordinate position

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    y, "``float`` Y-Axis value"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    
    // Set the Y-Axis coordinate of the object to 5

    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");

    obj.setPositionY(5);

|


BaseObject.setScale
=========================

Set object scale

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    x, "``float`` X-Axis value"
    y, "``float`` Y-Axis value"
    z, "``float`` Z-Axis value"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    
    // Set the scale of the object to be (1,2,3)

    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");

    obj.setScale(1,2,3);


|


BaseObject.setTransparent
=========================

Set object transparency.

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    trans, "``float`` transparency value range 0~1"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    // Set the object's transparency to'0.5'   

    object.create("AB052B5B646E4A48B9C045096FF9B088");
    
    obj.setTransparent(0.5);


|

BaseObject.stopAnim
=========================

Stop play object animation.

Parameters
^^^^^^^^^^^^
None



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    var obj =  object.create("0bcba8ca78734b64a3dae3eb699a913c");

    gui.createButton("Run", Rect(100, 100, 100, 30), function() {obj.playAnim("Run");});

    // Create a button named 'Stop'and set its size to (100,150,100,30). 
    // Pressing this button will stop object'obj'from playing the animation'Run'.

    gui.createButton("Stop", Rect(100, 150, 100, 30), function() {obj.stopAnim()});

|

BaseObject.stopMoving
=========================

Stop object moving.

Parameters
^^^^^^^^^^^^
None



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    var obj =  = object.create("AB052B5B646E4A48B9C045096FF9B088");

    obj.moveTo(Vector3(10, 0, 0), 5.0)

    // Create a button named 'Stop'and set its size to (100,150,100,30). 
    // Pressing this button will stop object'obj'from moving.

    gui.createButton("Stop", Rect(100, 150, 100, 30), function() {obj.stopMoving()});

|

BaseObject.transformPoint
==========================

Convert coordinates of object from relative coordinates to absolute coordinates

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    pos, "``Vector3`` relative coordinates of the object"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    // Create object'obj1, set its position (1,2,3)
    var obj  = object.create("AB052B5B646E4A48B9C045096FF9B088",Vector3(1,2,3));

    // Create a second object named'obj2'whose parent is'obj1'
    var obj2 = object.create("AB052B5B646E4A48B9C045096FF9B088",obj1,Vector3(4,5,6));

    print(obj2.transformPoint(Vector3(7,8,9)));


.. note::

    - The relative coordinates of'obj2'is (4,5,6)（Thus the absolute coordinates of'obj2'is ``(1,2,3)+(4,5,6)=(5,7,9)``
    
    -  Printing the transformPoint of Vector3(7,8,9) will show the value (12,15,18) (Converting the relative coordinates of Vector3 to absolute coordinates is ``(5,7,9)+(7,8,9)=(12,15,18))``


|

BaseObject.translate
==========================

Move a specified object to a specified direction and distance .

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    pos, "``Vector3``"



Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    // Create object'obj1, set its position (1,2,3)
    var obj  =  object.create("81807868C78141BFB2E93275AC3ABB39");

    // Create button *Button1*, If press this button, object obj's position add Vector3(1,0,1)
    
    var Button1= gui.createButton("translate", Rect(100, 200, 80, 50), function() {

    obj.translate(Vector3(1, 0, 1))});



    // Create a button named *Button2* Pressing on this button will move object'obj' position by a vector of (1,0,1)

    var Button2= gui.createButton("setPosition", Rect(100, 300, 80, 50), function() {

    obj.setPosition(Vector3(1, 0, 1))});

|


BaseObject.yaw
==========================

Rotate an object a specified degree around the Y-axis (clockwise)

Parameters
^^^^^^^^^^^^
.. csv-table::
    :header: Name, Description
    :widths: 5, 20

    degree, "``float`` rotation degree"


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    //Create an object named'obj'and rotate object'obj'a 45 degree angle around the Y-axis(clockwise).

    var obj  =  object.create("AB052B5B646E4A48B9C045096FF9B088");
    obj.yaw(45)










































