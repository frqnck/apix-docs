PHP
===

The PHP related documentation use the `phpdomain
<http://pypi.python.org/pypi/sphinxcontrib-phpdomain>`_ to provide custom
directives for describing PHP objects and constructs.

Describing classes and constructs
---------------------------------

Each directive populates the index, and or the namespace index.

.. rst:directive:: .. php:global:: name

   This directive declares a new PHP global variable.

.. rst:directive:: .. php:function:: name(signature)

   Defines a new global function outside of a class.

.. rst:directive:: .. php:const:: name

   This directive declares a new PHP constant, you can also use it nested
   inside a class directive to create class constants.

.. rst:directive:: .. php:exception:: name

   This directive declares a new Exception in the current namespace. The
   signature can include constructor arguments.

.. rst:directive:: .. php:class:: name

   Describes a class. Methods, attributes, and constants belonging to the class
   should be inside this directive's body::

        .. php:class:: MyClass

            Class description

           .. php:method:: method($argument)

           Method description


   Attributes, methods and constants don't need to be nested. They can also just
   follow the class declaration::

        .. php:class:: MyClass

            Text about the class

        .. php:method:: methodName()

            Text about the method


   .. seealso:: :rst:dir:`php:method`, :rst:dir:`php:attr`, :rst:dir:`php:const`

.. rst:directive:: .. php:method:: name(signature)

   Describe a class method, its arguments, return value, and exceptions::

        .. php:method:: instanceMethod($one, $two)

            :param string $one: The first parameter.
            :param string $two: The second parameter.
            :returns: An array of stuff.
            :throws: InvalidArgumentException

           This is an instance method.

.. rst:directive:: .. php:staticmethod:: ClassName::methodName(signature)

    Describe a static method, its arguments, return value and exceptions,
    see :rst:dir:`php:method` for options.

.. rst:directive:: .. php:attr:: name

   Describe an property/attribute on a class.
