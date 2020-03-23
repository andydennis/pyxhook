******************************
pyxhook basic doc tests
******************************

.. contents:: Table of Contents


Introduction
************

A simple example of hooking the keyboard on Linux using pyxhook.

Any key pressed prints out the key's values, program terminates when spacebar
is pressed.

Importing pyxhook
******************

Import relevant libraries.


    >>> import pyxhook
    >>> import time


Handle key presses
******************

Create a function that is called every time a key is presssed.

    >>> def kbevent(event):
    ...     global running
    ...     # print key info
    ...     print(event)
    ... 
    ...     # If the ascii value matches spacebar, terminate the while loop
    ...     if event.Ascii == 32:
    ...         running = False

Instantiate the HookManager object
**********************************

Create a HookManager object and store it in a
variable.

    >>> hookman = pyxhook.HookManager()

Define callbacks
****************

Define our callback to fire when a key is pressed down

    >>> hookman.KeyDown = kbevent


Capture keyboard input
**********************

Hook the keyboard

    >>> hookman.HookKeyboard()


Invoke a listener
*****************

Start our listener using the start methiod

    >>> hookman.start()

Loop the program 
*****************

Create a loop to keep the application running

    >>> running = True
    >>> while running:
    ...     time.sleep(0.1)

Exit the program
****************

Close the listener when we are done i.e. spacebar pressed

    >>> hookman.cancel()
