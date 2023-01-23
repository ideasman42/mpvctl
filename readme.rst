
######
MPVCTL
######

Command line access to ``mpv`` with extended functionality.

Required
========

- ``mpv``
- ``socat`` / ``nc``: ``socat`` preferred due to the differing implementations of netcat across UNIXes.


Usage
=====

``mpvctl`` requires the use of mpv and its `--input-ipc-server` option.

``mpvctl`` automatically opens an IPC-server for you when adding files to be played,
but by default will close the IPC-server when all files have finished playing.

To keep the ipc-server open permanently, use:

.. code-block:: sh

   $ mpv --input-ipc-server=/tmp/mpvsocket

You can also specify the default IPC server in your ``$XDG_CONFIG_HOME/mpv.conf``
which will make the most recent mpv instance you start be controllable via mpvctl:

.. code-block:: sh

   input-ipc-server=/tmp/mpvsocket


Help Text
=========

.. BEGIN HELP TEXT

Output of ``mpvctl --help``

usage::

       mpvctl [-h]

              ...

Utility to control mpv from the command line.

TIME FORMAT:
   For commands that accept TIME, valid time literals include.

   - ``10`` ten seconds.
   - ``-10m`` minus 10 minutes.
   - ``1.5h`` one and a half hours.
   - ``01:32:02`` one hour, 32minutes and 2 seconds.

options:
  -h, --help            show this help message and exit

subcommands:
  valid sub-commands


  :quit:                Quit the 'mpv' instance.
  :pause:               Stop playing.
  :play:                Start playing.
  :play-pause:          Toggle between play & pause.
  :next:                Play the next item in the playlist.
  :prev:                Play the previous item in the playlist.
  :seek:                Seek relative to the current playback position.
  :add:                 Add file(s) to the playlist.
  :trash-current:       Move the file that is currently playing to the trash.

Subcommand: ``quit``
--------------------

usage::

       mpvctl quit [-h]

options:
  -h, --help  show this help message and exit

Subcommand: ``pause``
---------------------

usage::

       mpvctl pause [-h]

options:
  -h, --help  show this help message and exit

Subcommand: ``play``
--------------------

usage::

       mpvctl play [-h]

options:
  -h, --help  show this help message and exit

Subcommand: ``play-pause``
--------------------------

usage::

       mpvctl play-pause [-h]

options:
  -h, --help  show this help message and exit

Subcommand: ``next``
--------------------

usage::

       mpvctl next [-h]

options:
  -h, --help  show this help message and exit

Subcommand: ``prev``
--------------------

usage::

       mpvctl prev [-h]

options:
  -h, --help  show this help message and exit

Subcommand: ``seek``
--------------------

usage::

       mpvctl seek [-h] TIME

positional arguments:
  TIME        Time string (see TIME format)

options:
  -h, --help  show this help message and exit

Subcommand: ``add``
-------------------

usage::

       mpvctl add [-h] [--replace] FILES [FILES ...]

positional arguments:
  FILES       One or more file-paths, with support for paths relative to the
              current working directory.

options:
  -h, --help  show this help message and exit
  --replace   Replace the current playlist instead of adding to the current
              playlist.

Subcommand: ``trash-current``
-----------------------------

usage::

       mpvctl trash-current [-h]

options:
  -h, --help  show this help message and exit

.. END HELP TEXT
