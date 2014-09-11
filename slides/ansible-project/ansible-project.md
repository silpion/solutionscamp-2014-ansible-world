<!SLIDE command bullets small>

# Infrastructure vs Project

## Infrastructure

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

# Infrastructure vs Project

## Project

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

# Infrastructure vs Project

## Project

### Git Repositories

* **Code** repository
* **Ansible** repository
* **Role** repositories
* **Project** repository

### Git Submodules

* **ansible/** submodules **Roles**
* **code/** submodules **ansible/**
* **project/** submodules **ansible/**



<!SLIDE command bullets small>

# Infrastructure vs Project

## Project

### Git Repositories

![Code repository](/file/assets/code-repository.png)



<!SLIDE command bullets small>

# Infrastructure vs Project

## Project

### Git Repositories

![Ansible repository](/file/assets/ansible-repository.png)



<!SLIDE command bullets small>

# Infrastructure vs Project

## Project

### Git Repositories

![Project repository](/file/assets/project-repository.png)



<!SLIDE command bullets small>

# Infrastructure vs Project

## Project

### Git Repositories

![The complete project](/file/assets/project.png)


<!-- vim: set nofen ts=4 sw=4 et: -->
