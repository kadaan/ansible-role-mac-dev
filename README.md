# Ansible Role: Mac-dev

[![Build Status](https://travis-ci.com/kadaan/ansible-role-mac-dev.svg?branch=master)](https://travis-ci.com/kadaan/ansible-role-mac-dev)

Mac developer box installation.

## Requirements

  - **Mac App Store account**: You can either sign into the Mac App Store via the GUI before running this role, or you can set the `mas_email` and `mas_password` prior to running the role. For security reasons, if you're going to use this role to sign in, you should use `vars_prompt` for at least the password; don't store unencrypted passwords with your playbooks!

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    homebrew_installed_packages: []

Packages you would like to make sure are installed via `brew install`.

    homebrew_upgrade_all_packages: true

Whether to upgrade homebrew and all packages installed by homebrew. If you prefer to manually update packages via `brew` commands, leave this set to `no`.

    homebrew_taps: []

Taps you would like to make sure Homebrew has tapped.

    homebrew_cask_apps: []

Apps you would like to have installed via `cask`. Search for popular apps on http://caskroom.io/ to see if they're available for install via Cask. Cask will not be used if it is not included in the list of taps in the `homebrew_taps` variable.

    atom_packages_packages: []

Packages you would like to make sure are installed in Atom.

    mas_email: ""
    mas_password: ""

The credentials for your Mac App Store account. The Apps you install should already be purchased by/registered to this account.

If setting these variables statically (e.g. in an included vars file), you should encrypt the inventory using [Ansible Vault](http://docs.ansible.com/ansible/playbooks_vault.html). Otherwise you can use [`vars_prompt`](http://docs.ansible.com/ansible/playbooks_prompts.html) to prompt for the password at playbook runtime.

If you leave both blank, and don't prompt for them, the role assumes you've already signed in via other means (e.g. via GUI or `mas signin [email]`), and will not attempt to sign in again.

    mas_installed_app_ids: []

A list of apps to ensure are installed on the computer. You can get IDs for all your existing installed apps with `mas list`, and you can search for IDs with `mas search [App Name]`.

    mas_upgrade_all_apps: true

Whether to run `mas upgrade`, which will upgrade all installed Mac App Store apps.

    node_versions: []

Node versions you would like to make sure are installed by nodenv.

    node_npm_global_packages: []

Global NPM packages you would like to make sure are installed.

    python_versions: []

Python versions you would like to make sure are installed by pyenv.

    python_pip_global_packages: []

Global PIP packages you would like to make sure are installed.

    ruby_versions: []

Ruby versions you would like to make sure are installed by rbenv.

    ruby_global_gems: []

Global Ruby gems you would like to make sure are installed.

## Dependencies

    - [kadaan.homebrew](https://galaxy.ansible.com/kadaan/homebrew/)
    - [kadaan.zplugin](https://galaxy.ansible.com/kadaan/zplugin/)
    - [kadaan.mas](https://galaxy.ansible.com/kadaan/mas/)
    - [kadaan.node](https://galaxy.ansible.com/kadaan/node/)
    - [kadaan.python](https://galaxy.ansible.com/kadaan/python/)
    - [kadaan.ruby](https://galaxy.ansible.com/kadaan/ruby/)
    - [hnakamur.atom-packages](https://galaxy.ansible.com/hnakamur/atom-packages/)

## Example Playbook

    - hosts: localhost
      roles:
        - { role: kadaan.mac-dev, macdev_execute: true }

## License

Apache 2.0
