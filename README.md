Buildmap
========

A GIS workflow pipeline for designing festivals. Buildmap takes a CAD
site plan in DXF format and produces a slippy map for viewing on the web.

A Diagram
=========

![buildmap diagram](/docs/diagram.png?raw=true)

Requirements
============

    apt-get install postgresql-9.4 postgresql-9.4-postgis-2.1 gdal-bin tilecache
    apt-get install python-jinja2 python-mapnik

You'll also need to install
[Magnacarto](https://github.com/omniscale/magnacarto) into your `$PATH`
(you only need the `magnacarto` binary and not the webapp).

Source Files
============

You will need at least one `.dxf` file to use as a source, and at least
one `.mss` (CartoCSS) file to control formatting. Each .mss file will
produce one output layer (which can be controlled on the OpenLayers
map).

Setup
=====

As the Postgres user:

    createuser buildmap
    createdb -O buildmap -EUNICODE [databasename]
    psql -d [databasename] -c "CREATE EXTENSION postgis;"

Allow your user to access the GIS database. The easiest (although not
necessarily most secure) way of doing this is to add the following line
to `pg_hba.conf`

    local   [databasename]         buildmap                   trust

Then test this with:

    psql -U buildmap [database name]

Now copy `config.py-example` to `config.py` and configure it.

Credits
=======

[Russ Garrett](https://github.com/russss)

This is an unrecognisably-refactored fork of Redlizard's work for OHM2013.