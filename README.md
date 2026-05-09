# ansible-sublime

An Ansible role for installing Sublime

### Requirements

This role requires two separate tools be installed.

First it requires the ansible.utils collection be installed from Ansible-Galaxy via:

```shell
ansible-galaxy collection install ansible.utils
```

Secondly it requires the jsonschema Python package be installed via:

```shell
pip install jsonschema
```

### Setup

Before the role can be used it needs to be added to the machine running the playbook, and as of writing this, this role is not hosted on Ansible-Galaxy only on Github.

1. Create a requirements.yml file in the root directory of the playbook being worked on.

2. Add the following definition inside the requirements.yml file:

```yaml
- name: hth-sublime
  src: https://github.com/hrafnthor/ansible-sublime.git
  scm: git
```

3. Install the requirements by executing

```shell
ansible-galaxy install -r .requirements.yml
```

This will allow any playbook run from this machine to use the role hth-sublime

#### Variables

All values are optional unless otherwise indicated.

```yaml
sublime:
  remove:   [boolean] Indicates if the package should be removed.
  signing:
    path:   [string]  Path to the repository pgp key. required in [signing] block.
    force:  [boolean] Indicates if the key should be forcefully updated.
  priority: [boolean] Indicates if the repository should have highest priority
```

##### Defaults variables

`hth_sublime_repository_signing_directory_path`:

The default path to where the repository signing key will be placed.

Defaults to `/etc/apt/keyrings/`.

`hth_sublime_repository_signing_key_filename`:

The default file name given to the repository signing key.

Defaults to `packages.sublime.org.asc`.

`hth_sublime_apt_preference_path`:

The default path to where the repository preference file will be placed.

Defaults to `/etc/apt/preferences.d/sublime`.

`hth_sublime_apt_repository_url`:

The default http url to the repository.

Defaults to `https://download.sublimetext.com/`.

`hth_sublime_user_config_path`:

The default user config directory path. This path is always relational to the user's home directory.

Defaults to `.config/sublime-text/Packages/User/`.

`hth_sublime_user_preference_filename`:

The default file name for user preference files.

Defaults to `Preferences.sublime-settings`.

`hth_sublime_user_keymap_filename`:

The default file name for user keympa files.

Defaults to `Default (Linux).sublime-keymap`.

### Example:

```yaml
- hosts: all
  vars:
    sublime:
      signing:
        path: "signing.asc"
        force: true
      priority: true
      version: 4192
      configs:
        - user: bob
          preferences: /sublime/bob/preferences
          keymap: /sublime/bob/keymap
  roles:
    - hth-sublime
```
