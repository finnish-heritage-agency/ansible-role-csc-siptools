ansible-role-csc-siptools
=========================

Ansible role for installing dpres-siptools and the required validation tools (eg. VeraPDF and JHove).

This Ansible role is only designed for CentOS 7, as that is the only Linux distribution supported by the DPRES service at the time of writing.

Configuration
-------------

Installation can be configured by changing the variables in `defaults/main.yml`.

Note that changing the installation directories for applications besides dpres-siptools will require changes to `file-scraper` dependency. This is not handled by this Ansible role at this time.
