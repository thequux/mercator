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
    (set simiter 10000)
    
    ; The results *should* be relatively resolution independent, but, as with any simulation, there may be subtle precision effects.
    (basemap (geodesic :iter 10 ; 10 subdivisions
                       :radius 6378k)) ; 6378 km radius. Mostly serves to scale featuresize

    (at 0 
      (squeezesphere 1 30k) ; Run sphere slicer 30k times, adding or removing 1 meter each time
      (flood 0)) ; flood all areas below elevation 0

    (defproc setup
      (squeezesphere 1 30k)
      (flood 0))
    (at 0 (invoke setup)) ; invoke runs a process once. start runs it until stopped

    ; Let's run a water sim
    (defproc watersim
      (set rainmap (rainfall (uniform 10))) ; drip a uniform (modulo noise) 10 cm of rain.
      (set flowmap (flow rainmap))
      (erode flowmap :hardness (uniform 10)))
    
    
Architecture
------------

The basemap is represented by a set of cells, each with a unique identifier, location, and set of neigbors.
