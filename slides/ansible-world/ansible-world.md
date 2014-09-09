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
          - "Infrastructure automation vs project automation"
          - "Ansible"
          - "Ansible - Test Driven"
          - "Ansible - Project automation"
      tasks:
        - name: Describe this talk
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



<!SLIDE>

This Page Intentionally Left Blank.



<!SLIDE command bullets small>

# Infrastructure automation vs Project automation

## Infrastructure automation

* Issues (e.g.)
    * Huge scope
        * Required knowledge about the complete infrastructure
        * Required planning for the complete infrastructure
        * Required time to implement *everything*
    * Risk
        * One change to rule them all
    * Resources
        * Number of projects?
        * Number of developers?
        * Number of system engineers?
        * Number of operators?
    * Processes
        * Not really management compatible
    * Priorities
        * Will *anything* get **really** done?
    * and
    * so
    * on
* Anyway better than managing things manualy!



<!SLIDE command bullets small>

# Infrastructure automation vs Project automation

## Project automation

* Scope?
    * It's about a project, not an infrastructure
* Risk?
    * One change to rule - eeh - *one* project
* Resources?
    * Time for **DevOps**
* Processes?
    * Perfectly fit in development processes
        * e.g. Scrum or Kanban
* Priorities?
    * Managable in development processes



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
