ansible-role-csc-siptools
=========================

Ansible role for installing dpres-siptools and the required validation tools (eg. VeraPDF and JHove).

This Ansible role is only designed for CentOS 7, as that is the only Linux distribution supported by the DPRES service at the time of writing.

Installation
------------

Create a `requirements.yml` file for your Ansible playbook and add the following lines:

```
- name: passari.csc_siptools
  src: https://github.com/finnish-heritage-agency/ansible-role-csc-siptools
```

Install the requirements using `ansible-galaxy`:

```
ansible-galaxy install -r requirements.yml
```

After this, you can use the installed role like any other role in your playbook:

```
- name: Install components
  hosts: worker
  roles:
    - common
    - database
    - passari.csc_siptools
    - backup
```

You must specify the `siptools_user` variable. This can be done when specifying
the role:

```
- name: Install siptools for 'bob'
  hosts: worker
  roles:
    - role: passari.csc_siptools
      vars:
        # required
        siptools_user: bob
        # optional, defaults to '/home/{{ siptools_user }}/dpres-siptools'
        siptools_install_path: "/home/bob/dpres-siptools"
```

Virtualenv containing the dpres-siptools and related Python packages will be installed in `{{ siptools_install_path }}/.venv`. You can use this path when installing dpres-siptools into a different virtualenv for use with Passari.

Configuration
-------------

List of variables you can change can be found in `defaults/main.yml`.

Note that changing the installation directories for applications besides dpres-siptools will require changes to `file-scraper` dependency. This is not handled by this Ansible role at this time.
