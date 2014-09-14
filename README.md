
## [![DebOps project](http://debops.org/images/debops-small.png)](http://debops.org) console



[![Travis CI](http://img.shields.io/travis/debops/ansible-console.svg?style=flat)](http://travis-ci.org/debops/ansible-console) [![test-suite](http://img.shields.io/badge/test--suite-ansible--console-blue.svg?style=flat)](https://github.com/debops/test-suite/tree/master/ansible-console/)  [![Ansible Galaxy](http://img.shields.io/badge/galaxy-debops.console-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/1556) [![Platforms](http://img.shields.io/badge/platforms-debian%20|%20ubuntu-lightgrey.svg?style=flat)](#)






This role manages console-related things, like enabling serial console,
setting up `/etc/motd` and `/etc/issue` files, configuring system-wide
locale settings. You can also provide a list of packages to install.





### Installation

This role requires at least Ansible `v1.7.0`. To install it, run:

    ansible-galaxy install debops.console

#### Are you using this as a standalone role without DebOps?

You may need to include missing roles from the [DebOps common
playbook](https://github.com/debops/debops-playbooks/blob/master/playbooks/common.yml)
into your playbook.

[Try DebOps now](https://github.com/debops/debops) for a complete solution to run your Debian-based infrastructure.








### Role variables

List of default variables available in the inventory:

    ---
    
    # Custom string added to /etc/issue
    console_issue: 'Organization Name'
    
    # Enable or disable serial console (allows you to use 'lxc-console',
    # 'virsh console' and other similar commands)
    console_serial: False
    
    # Serial console port
    console_serial_port: 'ttyS0'
    
    # Serial console baud rate
    console_serial_baud: '115200'
    
    # Serial console TERM string used to define terminal capabilities
    console_serial_term: 'xterm'
    
    # String used to enable serial console in sysvinit /etc/inittab
    console_serial_inittab: 'S0:2345:respawn:/sbin/getty -L {{ console_serial_port }} {{ console_serial_baud }} {{ console_serial_term }}'
    
    # Contents of /etc/motd
    console_motd: |
        -------------------------------------------------
                This system is managed by Ansible
        -------------------------------------------------
    
    # List of required console packages
    console_base_packages: [ 'locales' ]
    
    # List of additional packages to install
    console_packages: [ 'ncurses-term', 'vim', 'mc', 'ranger', 'tmux', 'zsh', 'htop',
                        'less', 'file', 'psmisc', 'iftop', 'nload', 'lsof' ]
    
    # Enable or disable FSCKFIX option in /etc/default/rcS
    # This option controls the behaviour of fsck during boot time, if it's enabled,
    # fsck will automatically repair filesystems without stopping the boot
    # process.
    # Choices: yes, no. Set to False to disable this feature.
    console_fsckfix: 'yes'
    
    # List of locales to enable on the host
    console_locales: [ 'en_US.UTF-8' ]









### Authors and license

`console` role was written by:

- Maciej Delmanowski | [e-mail](mailto:drybjed@gmail.com) | [Twitter](https://twitter.com/drybjed) | [GitHub](https://github.com/drybjed)

License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)



***

This role is part of the [DebOps](http://debops.org/) project. README generated by [ansigenome](https://github.com/nickjj/ansigenome/).
