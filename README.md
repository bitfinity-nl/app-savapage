Role Name
=========

SavaPage is an Open Print Portal that uses Open Standards and Commodity Hardware for Secure Pull-Printing, Pay-Per-Print, Delegated Print, Job Ticketing, Auditing and PDF Creation.
Requirements

Sources and credits goes to:
- https://www.savapage.org/

Requirements
------------

- Ubuntu 18.04LTS
- Postgresql

Role Variables
--------------

See default/main.yml for detailed information.


Dependencies
------------

- app-postgresql

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

    - hosts: savapaga-srv01
      become: true

      vars:

        # -- custom settings: app-savapage (postgresql) --
        sava_pgdb_state : 'enabled'
        sava_cups_ppd:
          - { src: 'http://download.example.com/resource/printers/taskalfa-2551ci/linux/English/Kyocera%20TASKalfa%202551ci.PPD',
              dest: '/usr/share/ppd/savapage/Kyocera TASKalfa 2551ci.PPD' }

        sava_cups_printers:
          - { name: 'printer1',
              ipaddress: '192.168.1.2',
              model: 'Kyocera TASKalfa 2551ci',
              ppd: /usr/share/ppd/savapage/Kyocera TASKalfa 2551ci.PPD,
              location: 'Office1' }
          - { name: 'printer2',
              ipaddress: '192.168.1.3',
              model: 'Kyocera TASKalfa 2551ci',
              ppd: /usr/share/ppd/savapage/Kyocera TASKalfa 2551ci.PPD,
              location: 'Office2' }

      roles:
        - app-postgresql
        - app-savapage




License
-------

GPLv3

Author Information
------------------

E: lrutten@bitfinity.nl

I: https://www.bitfinity.nl
