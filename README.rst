netaccess
=========

This command line application allows you to approve (or revoke) your machine's
internet access at IIT Madras.

Usage:
------

.. code:: bash

    netaccess
    netaccess (approve | revoke)
    netaccess revoke <ip address>
    netaccess -h | --help

Commands:
~~~~~~~~~

+---------------------+-----------------------------------------------------+
| approve             | Default command. Authenticates the current machine. |
+---------------------+-----------------------------------------------------+
| revoke <ip address> | Revokes the internet access of <ip address> (if you |
|                     | have previously approved it). Revokes the internet  |
|                     | access of current machine if no <ip address> is     |
|                     | provided.                                           |
+---------------------+-----------------------------------------------------+

Options:
~~~~~~~~

+-----------+-------------------------+
| -h --help | Shows the help message. |
+-----------+-------------------------+

