<!SLIDE command bullets small>

# Ansible - Test-driven development

## Components

* [Ruby](https://www.ruby-lang.org/en)
    * [Serverspec](http://serverspec.org)
* [Docker](https://docker.io) \|\| [Vagrant](https://www.vagrantup.com)
* ([ansible-tdd-generator](https://github.com/silpion/ansible-tdd-generator))



<!SLIDE command commandline bullets small>

# Ansible - Test-driven development

## ansible-tdd-generator

* Installs...
    * all necessary files to start writing integration tests
    * Docker and Vagrant environment for a single role

<!-- -->

    $ git clone https://github.com/silpion/ansible-tdd-generator
    Cloning into 'ansible-tdd-generator'...
    remote: Counting objects: 75, done.
    remote: Total 75 (delta 0), reused 0 (delta 0)
    Unpacking objects: 100% (75/75), done.
    Checking connectivity... done.
    $ cd ansible-tdd-generator
    $ ansible-playbook playbook.yml \
      -e role_name=foobar \
      -e role_path=/path/to/role


<!SLIDE command commandline bullets small>

# Ansible - Test-driven development

## ansible-galaxy init

* Installs
    * Ansible role boilerplate

<!-- -->

    $ ansible-galaxy init --init-path /tmp foobar
    foobar was created successfully

    $ ls /tmp/foobar
    .
    .
    .


<!-- vim: set nofen ts=4 sw=4 et: -->
