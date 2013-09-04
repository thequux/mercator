World generation
================

Generation script
-----------------

Lexical syntax
~~~~~~~~~~~~~~

Sample programs
~~~~~~~~~~~~~~~

.. code:: scheme

    (set randgen (rc4 "This is a random key"))
    ; The results *should* be relatively resolution independent, but, as with any simulation, there may be subtle precision effects.
    (basemap (geodesic 10)) # 10 subdivisions of a isocahedron

    ; The following 
    (at 0 
      (squeezesphere 0.01 1M))
