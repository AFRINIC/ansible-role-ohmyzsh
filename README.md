# Ansible Role: oh-my-zsh

Installs and configures the zsh shell and oh-my-zsh.


## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### ohmyzsh\_install\_users

A list of user accounts to update. All accounts listed will have `oh-my-zsh` installed as well as a .zshrc file copied into place.

Default: `ohmyzsh_install_users: []`

### ohmyzsh\_shell\_users

A list of accounts for whom the default shell should be updated too. These accounts will have the login shell changed to `zsh`.

Default: `ohmyzsh_shell_users: []`

### ohmyzsh\_theme
 
Which theme to use. See [oh-my-zsh/wiki/Themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes) for the choices. Currently this is a global setting for all user accounts affected. This role does not currently support setting themes per user.

Default `ohmyzsh_theme: gentoo`

### ohmyzsh\_aliases

Any aliases to add to the bottom of `.zshrc`. This is also global for all user accounts updated.

Default: `ohmyzsh_aliases: []`

### ohmyzsh\_plugins

A list of `oh-my-zsh` plugins to enable in `.zshrc`. This is also global for all user accounts updated. See the `oh-my-zsh` documentation for available plugins.

Default: `ohmyzsh_plugins: []`


## Example Playbook

    - hosts: all
      gather_facts: True
      roles:
        - { role: oh-my-zsh, ohmyzsh_install_users: [ zaphod ] }


## Credits

Forked from [opdavies/ansible-role-ohmyzsh](https://github.com/opdavies/ansible-role-ohmyzsh) - And updated to work on CentOS/EL based systems.

Additional changes noted below...


## Notes

This role has some unique design and implementation goals compared to the one it was forked from and other zsh/oh-my-zsh roles available.

It assumes that the target hosts may have limited direct Internet access and
also may or may not have the `git` command installed.

As such, it syncs a local copy of the `oh-my-zsh` repository from the role itself to the host. (Rather than from Github).

Of course this means that auto-updating is disabled. This also keeps the same version consistent across all your hosts, and only changes if you change the source in the role. But this may not suit everyone. You have been warned.


