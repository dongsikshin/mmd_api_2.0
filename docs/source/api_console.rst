***************
console
***************

Overview
=========

Manage control panel

.. csv-table::
    :header: Name, Description, Returns, Parameters
    :widths: 5, 15,5,10

    clear,	Clear text content,	none,	``console.clear()``
    log,	Print message on console platform,	none,	``console.log(obj)``
    show,	Hide or show console platform,	none,	``console.show(show)``
    

console.clear
=======================

Parameters
^^^^^^^^^^^^

None.


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    // Clear all text content on the console platform
    //Clear all text content on the control panel
    
    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");

    console.log(obj)

    console.clear()

|

console.log
=======================

Print output on **Control Panel**

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    obj, "``object``"


Example
^^^^^^^^^^ 

.. code-block:: javascript
   :linenos:

    //Print the scale of the object'obj'on the control panel
    var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
    console.log(obj.getScale())

|

console.show
=======================

Show or hide **Control Panel**

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    show, "``boolean``"


Example
^^^^^^^^^^ 

.. code-block:: javascript
   :linenos:

    print("show/hide control panel")

    gui.createButton("Platform shows:", Rect(100, 100, 200, 50), function() {console.show(true)});

    gui.createButton("Close platform", Rect(100, 200, 200, 50), function() {console.show(false)});


 

