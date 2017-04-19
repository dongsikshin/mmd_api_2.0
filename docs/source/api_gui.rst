***************
gui
***************

Control graphical user interface  within the scene

Overview
=========
.. csv-table::
    :header: Name, Description, Returns, Parameters
    :widths: 5, 15,5,10

    createbox,	Create a box,	``object``,	"``gui.createbox(text,rect)``"
    createButton,	Create a button,	``object``,	"``gui.createButton(text,rect,callback)``"
    createLabel,	Create a label,	``object``,	"``gui.createLabel(text, rect)``"
    createToggle,	Create a toggle button,	``object``,	"``gui.createToggle(checked,text,rect,callback)``"
    load,	Load an external GUI resource,	none,	"``gui.load(url,callback)``"

|

gui.createbox
=======================

Creat a graphical box

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    text, ``string`` text to display on the box
    rect,  ``rect`` a rectangle on the screen to use as the box
    callback, ``function`` callback function on mouse click


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    /** Create a GUI box called 'Box 1'. 
    Set the left coordinate to 100 pixels and the top coordinate to 200 pixels. 
    The width and height of the GUI Box is set to 80 pixels and 50 pixels respectively. */

    var obj = gui.createBox("Box 1", Rect(100, 200, 80, 50),function(){print("ok!")});

|

gui.createBox
=======================

Creat a button.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    text, ``string`` text to display on the box
    rect,  ``rect`` a rectangle on the screen to use as the box
    callback, ``function`` callback function on mouse click


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    /** Create a button. Set the left coordinate to 100 pixels and the top coordinate to 200 pixels. 
    The width and height of the button is set to 80 pixels and 50 pixels respectively. 
    Clicking on this button will print the string'You Clicked Button 1' */

    var buttont1 =  gui.createButton("Button 1", Rect(100, 200, 80, 50), function() {

    print ("You clicked Button 1");});

|



