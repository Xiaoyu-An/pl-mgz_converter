pl-mgz_converter
================================

.. image:: https://badge.fury.io/py/mgz_converter.svg
    :target: https://badge.fury.io/py/mgz_converter

.. image:: https://travis-ci.org/FNNDSC/mgz_converter.svg?branch=master
    :target: https://travis-ci.org/FNNDSC/mgz_converter

.. image:: https://img.shields.io/badge/python-3.5%2B-blue.svg
    :target: https://badge.fury.io/py/pl-mgz_converter

.. contents:: Table of Contents


Abstract
--------

``mgz_converter.py`` is a ChRIS-based application that takes Brain MRI images present in mgz format from the input directory, converts them to png & npy format and saves output to the output directory.


Synopsis
--------

.. code::

    python mgz_converter.py                                         \
        [-v <level>] [--verbosity <level>]                          \
        [--version]                                                 \
        [--man]                                                     \
        [--meta]                                                    \
        <inputDir>                                                  \
        <outputDir>                                                 \

Agruments
---------

.. code::

    [-v <level>] [--verbosity <level>]
    Verbosity level for app. Not used currently.

    [--version]
    If specified, print version number. 
    
    [--man]
    If specified, print (this) man page.

    [--meta]
    If specified, print plugin meta data.



Run
----

This ``plugin`` can be run in two modes: natively as a python package or as a containerized docker image.

Using ``docker run``
~~~~~~~~~~~~~~~~~~~~
To create the docker image, from the ``pl-mgz_converter`` directory run 

``docker build -t mgz_converter .``

To run using ``docker``, be sure to assign an "input" directory to ``/incoming`` and an output directory to ``/outgoing``. *Make sure that the* ``$(pwd)/out`` *directory is world writable!*

Now, prefix all calls with 

.. code:: bash
    mkdir in out && chmod 777 out
    docker run --rm -v $(pwd)/out:/outgoing                                                                 \
            pl-mgz_converter mgz_converter.py                           \
            /incoming /outgoing                                                                             

Thus, getting inline help is:

.. code:: bash

    mkdir in out && chmod 777 out
    docker run --rm -v $(pwd)/in:/incoming -v $(pwd)/out:/outgoing                                          \
            pl-mgz_converter mgz_converter.py                       \
            --man                                                                                           \
            /incoming /outgoing

Examples
--------

Convert mgz images to png & .npy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: bash

    mkdir in out && chmod 777 out
    docker run --rm -v $(pwd)/in:/incoming -v $(pwd)/out:/outgoing                                   \
            pl-mgz_converter mgz_converter.py                                    \
            /incoming /outgoing   


          


