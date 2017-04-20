***************
gui
***************

Control graphical user interface  within the scene

Overview
=========
.. csv-table::
    :header: Name, Description, Returns, Parameters
    :widths: 5, 15,5,10

    createBox,	Create a box,	``object``,	"``gui.createbox(text,rect)``"
    createButton,	Create a button,	``object``,	"``gui.createButton(text,rect,callback)``"
    createLabel,	Create a label,	``object``,	"``gui.createLabel(text, rect)``"
    createToggle,	Create a toggle button,	``object``,	"``gui.createToggle(checked,text,rect,callback)``"
    load,	Load an external GUI resource,	none,	"``gui.load(url,callback)``"

|

gui.createBox
=======================

Creat a button.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    text, ``string`` text to display on the button
    rect,  ``rect`` a rectangle on the screen to use as the button
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

gui.createLabel
=======================

Make a text or texture label.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    text, ``string`` text to display on the label
    rect,  ``rect`` a rectangle on the screen to use as the label


Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    /** Create a Label. Set the left coordinate to 100 pixels and the top coordinate to 200 pixels. 
    The width and height of the label is set to 80 pixels and 50 pixels respectively.*/

   gui.createLabel("Label 1", Rect(100, 200, 80, 50));

|

gui.createToggle
=======================

Make an on/off toggle button

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    checked, "``Boolean`` set initial status to 'On' or 'Off'"
    text, ``string`` text to display on the toggle
    rect,  ``rect`` a rectangle on the screen to use as the toggle button
    callback, ``function`` callback function on mouse click

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    /** Create a Toggle Button. Set the left coordinate to 100 pixels and the top coordinate to 200 pixels. 
    The width and height of the GUI Box is set to 80 pixels and 50 pixels respectively. 
    If the value of the Toggle Button is changed, print the string'You clicked Toggle 1' */

    gui.createToggle ("Toggle 1", Rect(100, 200, 80, 50), function() {
        print("You changed the state of Toggle 1");}
    );

|

gui.load
=======================

Load GUI resource.

Parameters
^^^^^^^^^^^^

.. csv-table::
    :header: Name, Description
    :widths: 5, 15

    url,  ``string`` resource url
    callback, ``function`` callback function on mouse click

Example
^^^^^^^^^^

.. code-block:: javascript
   :linenos:

    /** GUI resource from the specified URL. After the GUI has loaded, 
      print 'Successfully loading resource from url! */

    var url = "http://www.3dmomoda.com/mmdclient/script/examples/demos/scifi_ui.bundle"
    gui.load(url, function(){print("Successfully loading resource from url！")});





