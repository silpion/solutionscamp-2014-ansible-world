<!SLIDE title>

<!-- -->

<!SLIDE command commandline small>

# Ansible world

## whoami

    $ cat whoami.yml
    ---
    - hosts: localhost
      connection: local
      gather_facts: false
      vars:
        - presenter:
            name: Mark Kusch
            mail: kraM@silpion.de
            notes: "I have no idea what I'm doing"
      tasks:
        - name: Tell the world who I am
          debug: msg="I am {{ presenter.name }} <{{ presenter.mail }}>"


    $ ansible-playbook -i hosts whoami.yml

    PLAY [localhost] **************************************************************

    TASK: [Tell the world who I am] ***********************************************
    ok: [localhost] => {
        "msg": "I am Mark Kusch <kraM@silpion.de>"
    }

    PLAY RECAP ********************************************************************
    localhost                  : ok=1    changed=0    unreachable=0    failed=0



<!SLIDE command commandline small>

# Ansible world

## Overview

    $ cat overview.yml
    ---
    - hosts: localhost
      connection: local
      gather_facts: false
      vars:
        - topics:
          - "Requirements"
          - "Ansible"
          - "Ansible - Test Driven"
          - "Ansible - Infrastructure vs Project"
          - "Ansible - The foo project"
      tasks:
        - name: Describe this session
          with_items: topics
          debug: msg="{{ item }}"



<!SLIDE command commandline small>

# Ansible world

## Requirements

    $ cat requirements.yml
    ---
    - hosts: localhost
      connection: local
      gather_facts: true
      vars:
        - requirements:
          - name: git
            url: http://git-scm.com
          - name: python2
            url: https://python.org
          - name: ansible
            url: https://ansible.com
          - name: ruby
            url: https://www.ruby-lang.org/en
          - name: serverspec
            url: http://serverspec.org
          - name: docker
            url: https://docker.io
          - name: vagrant
            url: https://www.vagrantup.com
      tasks:
        - name: Install requirements
          with_items: requirements
          action: "{{ ansible_pkg_mgr }} state=installed name={{ item.name }}"



<!SLIDE blank>

This Page Intentionally Left Blank.



<!SLIDE command bullets small>

# Ansible

* *Infrastructure in data*
* Written in [Python](http://python.org)(2)
* Uses [YAML](http://yaml.org) as description language
    * No additional DSL to learn
* No infrastructure requirements (except for SSH)
* Generates Python code
    * Copies generated code to managed node through SSH
    * Runs generated code on managed node through SSH
    * Removes traces on managed node



<!SLIDE command bullets small>

# Ansible

## Glossary

* *roles*
    * Collection of tasks and default configuration data
        * chef := cookbook
        * puppet := manifest
* *playbook*
    * Assemble roles for a set of nodes
* *inventory*
    * Heart of Ansible
        * Maintain nodes to manage
        * Maintain configuration data to configure roles for nodes


<!-- vim: set nofen sw=4 ts=4 et: -->
