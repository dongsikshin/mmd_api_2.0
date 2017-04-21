***************
ScriptObject
***************

Overview
=========

Control all the scripts associated with objects. script may implements two object interface: ``Start`` and/or ``Update``

.. csv-table::
    :header: Name, Description, Returns, Parameters
    :widths: 5, 15,5,10

    Start,	"called before any object updates, just once", none, "``Start({script})``"
    Update,	"called per frame", none, "``Update({script})``"


Start
================

Parameters
^^^^^^^^^^

None


Exmaple
^^^^^^^^^^

.. code-block:: javascript
   :linenos:


    //Create a Start function, this function defines the initial speed of an object 
    //to a random float between 1 to 8
    AutoRtate = {
        speed : 0,
        objOption : null,
        function Start() {this.speed = util.randomFloat(1, 8);}

        // Create an Update function, 
        //this function rotates the object a random degree along the Y-Axis every frame.
        function Update() {this.objOption.yaw(this.speed); }
    }

    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088", Vector3(2.5, 0, 0));

    var script = obj.addScript(AutoRtate,"rotation");

    script.objOption = obj;



|

Update
================

Parameters
^^^^^^^^^^

None.


Exmaple
^^^^^^^^^^

.. code-block:: javascript
   :linenos:


    //Create a Start function, this function defines the initial speed of an object 
    //to a random float between 1 to 8
    AutoRtate = {
        speed : 0,
        objOption : null,
        function Start() {this.speed = util.randomFloat(1, 8);}

        // Create an Update function, 
        //this function rotates the object a random degree along the Y-Axis every frame.
        function Update() {this.objOption.yaw(this.speed); }
    }

    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088", Vector3(2.5, 0, 0));

    var script = obj.addScript(AutoRtate,"rotation");

    script.objOption = obj;


