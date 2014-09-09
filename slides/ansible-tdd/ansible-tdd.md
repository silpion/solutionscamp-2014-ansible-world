<!SLIDE command bullets small>

# Ansible - Test-driven development

## Components

* [Ruby](https://www.ruby-lang.org/en)
    * [Bundler](http://bundler.io)
    * [Serverspec](http://serverspec.org)
* [Docker](https://docker.io) \|\| [Vagrant](https://www.vagrantup.com)
* ([ansible-tdd-generator](https://github.com/silpion/ansible-tdd-generator))



<!SLIDE command commandline small>

# Ansible - Test-driven development

## ansible-galaxy init

* Install Ansible role boilerplate

<!-- -->

    $ ansible-galaxy init --init-path /tmp ansible-foobar
    ansible-foobar was created successfully

    $ ls /tmp/ansible-foobar
    .
    .
    .


<!SLIDE command commandline bullets small>

# Ansible - Test-driven development

## ansible-tdd-generator

* Installs...
    * all necessary files to start writing integration tests
    * Docker and Vagrant environments for a single role
* Targets...
    * working environments at Silpion
        * Role directories are called *ansible-ROLENAME*
* Requires...
    * some love for more customization
    * flexibility to add intgration test infrastructure to projects

<!-- -->

    $ git clone https://github.com/silpion/ansible-tdd-generator
    Cloning into 'ansible-tdd-generator'...
    remote: Counting objects: 75, done.
    remote: Total 75 (delta 0), reused 0 (delta 0)
    Unpacking objects: 100% (75/75), done.
    Checking connectivity... done.



<!SLIDE command commandline small>

# Ansible - Test-driven development

## ansible-tdd-generator on foobar role

    $ ansible-playbook playbook.yml -e role_name=foobar -e role_path=/tmp/ansible-foobar

    PLAY [localhost] **************************************************************

    TASK: [Verify user input for variables] ***************************************
    ok: [localhost]

    TASK: [Install .gitignore] ****************************************************
    changed: [localhost -> 127.0.0.1]

    TASK: [Install directories for Ansible TDD] ***********************************
    changed: [localhost -> 127.0.0.1] => (item=rake)
    changed: [localhost -> 127.0.0.1] => (item=spec/default)
    changed: [localhost -> 127.0.0.1] => (item=spec/lib)
    changed: [localhost -> 127.0.0.1] => (item=tests)

    TASK: [Install static files for Ansible TDD] **********************************
    changed: [localhost -> 127.0.0.1] => (item=ansible.cfg)
    changed: [localhost -> 127.0.0.1] => (item=Gemfile)
    changed: [localhost -> 127.0.0.1] => (item=rake/docker.rb)
    changed: [localhost -> 127.0.0.1] => (item=rake/vagrant.rb)
    changed: [localhost -> 127.0.0.1] => (item=Rakefile)
    changed: [localhost -> 127.0.0.1] => (item=spec/lib/docker.rb)
    changed: [localhost -> 127.0.0.1] => (item=spec/lib/vagrant.rb)
    changed: [localhost -> 127.0.0.1] => (item=spec/spec_helper.rb)
    changed: [localhost -> 127.0.0.1] => (item=tests/hosts)
    changed: [localhost -> 127.0.0.1] => (item=tests/silpion-insecure-private-key)

    TASK: [Install templates for Ansible TDD] *************************************
    changed: [localhost -> 127.0.0.1] => (item=tests/docker.yml)
    changed: [localhost -> 127.0.0.1] => (item=tests/playbook.yml)
    changed: [localhost -> 127.0.0.1] => (item=Vagrantfile)

    TASK: [Install spec integration test file] ************************************
    changed: [localhost -> 127.0.0.1]

    PLAY RECAP ********************************************************************
    localhost                  : ok=6    changed=5    unreachable=0    failed=0



<!SLIDE command commandline small>

# Ansible - Test-driven development

## bundle install

    $ bundle install


## rake suite

    $ rake suite
    $ # ||
    $ RAKE_ANSIBLE_USE_VAGRANT=1 rake suite


## rake targets

    $ rake lint # default
    $ rake up
    $ rake provision
    $ rake spec
    $ rake clean
    $ rake ssh
    $ rake suite


## Workflow

    $ $EDITOR spec/default/foobar_spec.rb
    $ # code
    $ rake provision
    $ rake spec


<!-- vim: set nofen ts=4 sw=4 et: -->
