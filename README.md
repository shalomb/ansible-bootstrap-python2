ansible-bootstrap-python2
=========================

- [`master`](https://github.com/shalomb/ansible-bootstrap-python2/tree/master)   [![Build Status](https://travis-ci.org/shalomb/ansible-bootstrap-python2.svg?branch=master)](https://travis-ci.org/shalomb/ansible-bootstrap-python2/branches)
- [`develop`](https://github.com/shalomb/ansible-bootstrap-python2/tree/develop) [![Build Status](https://travis-ci.org/shalomb/ansible-bootstrap-python2.svg?branch=develop)](https://travis-ci.org/shalomb/ansible-bootstrap-python2/branches)

Ansible role to
[bootstrap the installation of python
2.x](https://gist.github.com/gwillem/4ba393dceb55e5ae276a87300f6b8e6f#gistcomment-2167540)
when it is not available.

As ansible depends on python 2.x for normal execution, this role
performs the installation of python making use of distro-specific
installation commands under the
[`raw`](http://docs.ansible.com/ansible/latest/raw_module.html)
module.

Requirements
------------

- To succeed, the enclosing play has to ensure `gather_facts: False`

Role Variables
--------------

    refresh_repositories: False

Refresh/Update the package cache before installation, it is necessary
to set this to `True` when targets are created from slim/docker images.

Example Playbook
----------------

    - name: Install python-minimal
      hosts: all
      any_errors_fatal: True
      gather_facts: no
      become: True
      roles:
        - name: ansible-bootstrap-python2
          refresh_repositories: True
      tags:
        - bootstrap
        - python2

Also see [tests/test.yml](tests/test.yml) for better examples.

