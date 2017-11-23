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

Using Snap
~~~~~~~~~~

For those of you who don't want to go through the trouble of installing Rust
and Cargo, I have created a snap_ package which should work on most Linux
distributions. After `setting up snap`_, you can install this application by

.. code:: bash

   $ sudo snap install netaccess


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
| approve             | Default command. Approves internet access of        |
|                     | current machine.                                    |
+---------------------+-----------------------------------------------------+
| revoke <ip address> | Revokes internet access of <ip address> (if you     |
|                     | have previously approved it). Revokes internet      |
|                     | access of current machine if no <ip address> is     |
|                     | provided.                                           |
+---------------------+-----------------------------------------------------+

Options:
~~~~~~~~

+---------------+---------------------------+
| -h, --help    | Shows the help message.   |
+---------------+---------------------------+
| -V, --version | Shows version information |
+---------------+---------------------------+


.. |build-status| image:: https://api.travis-ci.org/j-jith/iitm-netaccess-cmd.svg?branch=master
                  :target: https://travis-ci.org/j-jith/iitm-netaccess-cmd

.. |snap-status| image:: https://build.snapcraft.io/badge/j-jith/iitm-netaccess-cmd.svg
                 :target: https://build.snapcraft.io/user/j-jith/iitm-netaccess-cmd

.. _Rust: https://www.rust-lang.org

.. _Cargo: http://doc.crates.io/

.. _snap: https://snapcraft.io/

.. _setting up snap: https://docs.snapcraft.io/core/install
