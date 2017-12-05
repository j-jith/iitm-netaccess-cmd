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

    netaccess [OPTIONS] [SUBCOMMAND]

Flags
~~~~~

.. code::

    -h, --help       Prints help information
    -V, --version    Prints version information

Options
~~~~~~~

.. code::

    -d, --duration <duration>    (Optional) Duration of approval - 1 => one hour, 2 => one day. Omit to be prompted.
    -p, --password <password>    (Optional) Password associated with your username. Omit to be prompted.
    -u, --username <username>    (Optional) Username (your roll number) used for logging in to netaccess. Omit to be prompted.

Subcommands
~~~~~~~~~~~

.. code::

    approve    Approve internet access for this machine. Invoked by default if no subcommands are specified.
    help       Prints this message or the help of the given subcommand(s)
    revoke     Revoke internet access of this or other previously approved machine(s)

Examples
~~~~~~~~

If you simply call ``netaccess`` without any subcommands/options, you
will be prompted for all requisite data.

.. code::

   $ netaccess
   Username: ddyyb000
   Password:
   Session duration (1: one hour (default), 2: one day): 2
   You have requested approval for one day
   Login successful
   Succesfully approved

Alternatively, you can use the options ``-u``, ``-p``, and ``-d`` to
specify your username, password, and duration of approval,
respectively, at the time of calling `netaccess`.

.. code::

   $ netaccess -u ddyyb000 -p my_password -d 2
   Login successful
   Succesfully approved

The above command is equivalent to

.. code::

   $ netaccess approve -u ddyyb000 -p my_password -d 2

``approve`` is the default subcommand. So you can omit it if you don't
feel like typing a lot.

.. caution::

    Please note that it is not recommended to provide your password in plain text
    using the ``-p`` option. A password manager should be used for this purpose.
    Please see `Using the password option`_.

To revoke internet access of your machine, you can simply type

.. code::

   $ netaccess revoke

You will be prompted for your username and password. This will be
followed by a prompt for your network interface. This is required to
identify your IP address. If you are aware of your IP address, you can
do the following

.. code::

   $ netaccess revoke <ip address>

You can revoke internet access of any machine that you've previously
approved. At the moment, ``revoke`` subcommand does not validate the
IP address. So you have to be careful when entering the IP
address. ``revoke`` command can also accept username and password
through ``-u`` and ``-p`` as follows

.. code::

   $ netaccess revoke <ip address> -u ddyyb000 -p my_password

Using the password option
~~~~~~~~~~~~~~~~~~~~~~~~~

It is not recommended to provide your password to the ``-p`` option in plain
text for the sake of security. Instead, a password manager like pass_ should be
used. In ``pass``, one can create an entry for netaccess by

.. code::

   $ pass insert netaccess

Then, the password can be provided to ``netaccess`` as follows.

.. code::

   $ netaccess approve -u ddyyb000 -d 2 -p `pass netaccess`

Of course, if you don't want to store the password on your machine, you can
simply omit the ``-p`` option, and you'll be prompted for your password.


.. |build-status| image:: https://api.travis-ci.org/j-jith/iitm-netaccess-cmd.svg?branch=master
                  :target: https://travis-ci.org/j-jith/iitm-netaccess-cmd

.. |snap-status| image:: https://build.snapcraft.io/badge/j-jith/iitm-netaccess-cmd.svg
                 :target: https://build.snapcraft.io/user/j-jith/iitm-netaccess-cmd

.. _Rust: https://www.rust-lang.org

.. _Cargo: http://doc.crates.io/

.. _snap: https://snapcraft.io/

.. _setting up snap: https://docs.snapcraft.io/core/install

.. _pass: https://www.passwordstore.org/
