..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell. Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts. A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. index:: dot notation, methods

Adding Other Methods to our Class
---------------------------------

The key advantage of using a class like ``Point`` rather than something like a simple tuple ``(7, 6)`` now becomes apparent. We can add methods to the ``Point`` class that are sensible operations for points. Had we chosen to use a simple tuple to represent the point, we would not have this capability. Creating a class like ``Point`` brings an exceptional amount of "organizational power" to our programs, and to our thinking. We can group together the sensible operations and the kinds of data they apply to, and each instance of the class can have its own state.

A **method** behaves like a function but it is invoked on a specific instance. For example, with a turtle named ``tess``, ``tess.right(90)`` asks the ``tess`` object to perform its ``right`` method and turn 90 degrees. Methods are accessed using dot notation.

Let's add two simple methods to allow a point to give us information about its state. The ``get_x`` method, when invoked, will return the value of the x coordinate. The implementation of this method is straight forward since we already know how to write functions that return values. One thing to notice is that even though the ``get_x`` method does not need any other parameter information to do its work, there is still one formal parameter, ``self``.  As we stated earlier, all methods defined in a class that operate on objects of that class will have ``self`` as their first parameter. Again, this serves as reference to the object itself which in turn gives access to the state data inside the object.

.. activecode:: chp13_classes4

    class Point:
        """ Point class for representing and manipulating x,y coordinates. """

        def __init__(self, init_x, init_y):
            """ Create a new point at the given coordinates. """
            self.x = init_x
            self.y = init_y

        def get_x(self):
            return self.x

        def get_y(self):
            return self.y


    p = Point(7, 6)
    print(p.get_x())
    print(p.get_y())

Note that the ``get_x`` method simply returns the value of ``self.x`` from the object itself. In other words, the implementation of the method is to go to the state of the object itself and get the value of ``x``.  Likewise, the ``get_y`` method looks the same.

Let's add another method, ``distance_from_origin``, to see better how methods work. This method will not need any additional information to do its work, but it will perform a more complex task.


.. activecode:: chp13_classes5

    class Point:
        """ Point class for representing and manipulating x,y coordinates. """

        def __init__(self, init_x, init_y):
            """ Create a new point at the given coordinates. """
            self.x = init_x
            self.y = init_y

        def get_x(self):
            return self.x

        def get_y(self):
            return self.y

        def distance_from_origin(self):
            return ((self.x ** 2) + (self.y ** 2)) ** 0.5


    p = Point(7, 6)
    print(p.distance_from_origin())



Notice that the caller of ``distance_from_origin`` does not explicitly supply an argument to match the ``self`` parameter. This is true of all method calls. The definition will always have one additional parameter as compared to the invocation.
