netaccess
=========

|build-status| |snap-status|

This command line application allows you to login to IIT Madras' netaccess
website and approve (or revoke) your machine's internet access.

Installation
------------

Using Cargo
~~~~~~~~~~~

This application is written in Rust_, and therefore the easiest way to install
it is using the Cargo_ package manager of Rust. Installation is as simple as

.. code:: bash

   $ cargo install --git https://github.com/j-jith/iitm-netaccess-cmd


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


.. |build-status| image:: https://img.shields.io/travis/j-jith/iitm-netaccess-cmd.svg
                  :target: https://travis-ci.org/j-jith/iitm-netaccess-cmd

.. |snap-status| image:: https://build.snapcraft.io/badge/j-jith/iitm-netaccess-cmd.svg
                 :target: https://build.snapcraft.io/user/j-jith/iitm-netaccess-cmd

.. _Rust: https://www.rust-lang.org

.. _Cargo: http://doc.crates.io/
