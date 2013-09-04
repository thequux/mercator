========
Mercator
========
--------------
A mapping tool
--------------


Metadata
========
:Working-name: mercator
:Working-url: mercator.uh

Introduction
============

Cartographer is intended to make it easy for novices to build
high-quality maps of fictional places collaboratively over the
internet, and provide a rich tapestry of tools for presenting these
created worlds.

At the very minimum, it will provide an OSM-compatible API that can be
edited using tools such as Potlatch and JOSM, and an openlayers-based
slippy map that can be shared with people not immediately involved in
the project. Ideally, map rendering will be customizable using
stylesheets, and artifacts such as stylized train maps, train
schedules, and even 3-d renderings of the virtual world can be created
directly from the underlying GIS datastore.


Interface (programmatic)
========================

Suppose that there exists a mapping project named koana-islands

OSM-compatible API
    https://api.koana-islands.mercator.uh

Tileserver
    https://tiles.koana-islands.mercator.uh/<tileset>
  
Viewer and other admin tools
    https://koana-islands.mercator.uh/


Architecture
============

Postgresql/PostGIS
------------------
Stores the underlying GIS data. Stored in OSM apidb
format
  
Modifications
  - Add projects table
  - add links to projects table to any resources that are project specific (i.e, nodes, ways, etc)

OSM API
-------

Modifications
  - Choose project based on hostname, thread project name through code.

Map provider
------------

Built out of the following tools, in no particular order

- Carto_
- Mapnik_
- Millstone_
- TileLive_
- TileLive-Mapnik_

.. _Mapnik: https://github.com/mapnik/mapnik
.. _Millstone: https://github.com/mapbox/millstone
.. _Carto: https://github.com/mapbox/carto
.. _TileLive: https://github.com/mapbox/tilelive.js
.. _TileLive-Mapnik: https://github.com/mapbox/tilelive-mapnik

Modifications
  TileLive-Mapnik
    - XML file search will be replaced by "load from DB"
  Millstone
    - Resolve resources from DB, rather than FS

UI
--

Custom-written, possibly based on OSM ui. We'll probably at least pull in iD_ and Potlatch2_

.. _iD: https://github.com/systemed/iD/
.. _Potlatch2: https://github.com/openstreetmap/potlatch2

Will provide at least

World generation
----------------

Likely going to need to be custom-written.

Requirements:
  - batch process
  - Results completely specified by the input
    - Includes RNG, etc
  - command file, rather than switches (inputs will tend to be long)

See [World generation](world-generation.html)

Resources
=========

http://weait.com/content/build-your-own-openstreetmap-server-lucid
