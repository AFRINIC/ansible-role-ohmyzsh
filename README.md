# Ansible Role: oh-my-zsh

Installs and configures the zsh shell and oh-my-zsh.


## Credits

Forked from [opdavies/ansible-role-ohmyzsh](https://github.com/opdavies/ansible-role-ohmyzsh) - And updated to work on CentOS/EL based systems.


## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### ohmyzsh\_copy\_zshrc

Whether to set copy a .zshrc file. This can be set to `false` if you already have your own copy.

Default: `ohmyzsh_copy_zshrc: true`

### ohmyzsh\_change\_shell

Whether to change the default shell for the specified user accounts.

Default: `ohmyzsh_change_shell: false`

### ohmyzsh\_users

A list of user accounts to update.

Default: `ohmyzsh_users: []`

### ohmyzsh\_theme
 
Which theme to use. See [oh-my-zsh/wiki/Themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes) for the choices.

Default `ohmyzsh_theme: gentoo`

### ohmyzsh\_aliases

Any aliases to add to the bottom of `.zshrc`.

Default: `ohmyzsh_aliases: []`


## Example Playbook

    - hosts: all
      roles:
        - { role: oh-my-zsh, ohmyzsh_users: [ zaphod ] }


## Notes

The other change that has been made from the original version is to sync the oh-my-zsh repository from a local copy, rather that from the source on Github.

This is to allow provisioning to many hosts, but avoiding re-getting from the outside internet over and over again.

This is a design goal of this fork, but the downside is that it effectively breaks oh-my-zsh's update feature. This is also intended as a feature not a bug, as it keeps the same version consistent across all your hosts, and only changes if you change the source in the role. But this may not suit everyone. You have been warned.

