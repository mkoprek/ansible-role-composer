[![Build Status](https://travis-ci.com/mkoprek/ansible-role-composer.svg?branch=main)](https://travis-ci.com/mkoprek/ansible-role-composer)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-composer-blue.svg?style=flat)](https://galaxy.ansible.com/mkoprek/composer)

Composer Ansible Role
=========
Role for install composer package manager

Requirements
------------
This role requires Ansible 2.4 or higher and tested platforms:
* ubuntu:focal
* ubuntu:bionic
* debian:buster
* debian:stretch

- `php` - MUST be installed for run composer. You can use `mkoprek.phpfpm` role for install it.

Role Variables
--------------
All defaults variables are available in defaults/main.yml:

```yaml
composer_installer_url: https://getcomposer.org/installer
composer_installed_sha_url: https://composer.github.io/installer.sig
```
Standard urls for download composer-installer.php and it signature

```yaml
composer_version: ''
composer_latest_major_version: --2

```
If `composer_version` is set composer-install will try to install specific version.
If you want to stick with composer 1.* you need to set `composer_latest_major_version` to `--1`

```yaml
composer_install_path: /usr/local/bin/
composer_install_name: composer
```
Path where composer will be installed and with what name

```yaml
composer_home_path: ~/.composer
composer_user: root
composer_group: root
```
Path where composer will store data and install global packages
If you need install composer as different user you can also change it here

```yaml
composer_github_oauth: ''
```
If you need to avoid GitHub limits you need to specify here GitHub OAuth

```yaml
composer_global_packages: []
composer_home_path_add_to_path: false
```
If you need to install any of packages globally you can add it here as a list
Also if you need have access for those packages you can switch `composer_home_path_add_to_path` to true

Requirements
------------
Role requires installed `git` and it will be installed during play.

Example Playbook
----------------
Example usage when you need to install composer in specific 1.10.20 version:

    - hosts: servers
      roles:
         - role: username.rolename
           vars:
             composer_version: 1.10.20  

License
-------
MIT

Author Information
------------------
Role created by Maciej Koprek (mkoprek) 2021
