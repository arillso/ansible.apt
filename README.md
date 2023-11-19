# Ansible Role: apt

## Important Update

Please note that the ansible.users role has been moved to a new collection and will no longer be actively developed in this repository.
For the latest version of the role, including new features and updates, please visit the new collection at <https://github.com/arillso/ansible.system/tree/main/roles/apt_configuration>.
We encourage all users to switch to the updated role in the new collection for ongoing support and improvements.

## Description

This role optimizes the package manager apt and under Debian/Ubuntu. It can be determined how long the packages will be cached, how often he should check for updates and when he should install the updates automatically.

## Installation

```bash
ansible-galaxy install arillso.apt
```

## Requirements

## Role Variables

### Archives

Whether the cache of DEB files should be preserved or cleaned

```yml
apt_preserve_cache: 'no'
```

Max age (in days) of DEB files to keep when cleaning cache

```yml
apt_archives_maxage: null
```

Min age (in days) of DEB files to keep when cleaning cache

```yml
apt_archives_minage: null
```

Max size (in MB) of DEB files to keep when cleaning cache

```yml
apt_archives_maxsize: null
```

### General

whether or not suggested packages should be installed

```yml
apt_install_suggests: 'no'
```

do not install Recommended packages by default

```yml
apt_install_recommends: 'no'
```

allow 'apt-get autoremove' to remove recommended packages

```yml
apt_remove_recommends: 'no'
```

Enable the update/upgrade script

```yml
apt_periodic: 'yes'
```

Do “apt-get update” automatically every n-days (0=disable)

```yml
apt_update_package_lists: 1
```

Do “apt-get upgrade –download-only” every n-days (0=disable)

```yml
apt_download_upgradeable_packages: 0
```

Do “apt-get autoclean” every n-days (0=disable)

```yml
apt_auto_clean_interval: 0
```

### unattended-upgrades

enable unattended-upgrades

```yml
apt_unattended_upgrades: 'yes'
```

list of packages to not update (regexp are supported)

```yml
apt_unattended_upgrades_blacklist: []
```

Split the upgrade into the smallest possible chunks so that they can be interrupted with SIGUSR1. This makes the upgrade a bit slower but it has the benefit that shutdown while a upgrade is running is possible (with a small delay)

```yml
apt_unattended_upgrades_minimal_steps: 'no'
```

Send email to this address for problems or packages upgrades If empty or unset then no email is sent, make sure that you have a working mail setup on your system. A package that provides 'mailx' must be installed. E.g. "<user@example.com>"

```yml
apt_mails: []
```

Set this value to "true" to get emails only on errors. Default is to always send a mail if Unattended-Upgrade::Mail is set

```yml
apt_unattended_upgrades_notify_error_only: 'yes'
```

Do automatic removal of new unused dependencies after the upgrade (equivalent to apt-get autoremove)

```yml
apt_unattended_upgrades_autoremove: 'yes'
```

Automatically reboot _WITHOUT CONFIRMATION_ if the file /var/run/reboot-required is found after the upgrade

```yml
apt_unattended_upgrades_automatic_reboot: 'no'
```

If automatic reboot is enabled and needed, reboot at the specific time instead of immediately
Values: now | 02:00 | ...

```yml
apt_unattended_upgrades_automatic_reboot_time: now
```

## Dependencies

## Example Playbook

```yml
- hosts: all
  roles:
    - arillso.apt
```

## Author

- [Simon Bärlocher](https://sbaerlocher.ch)

## Inspiration

- [We Are Interactive](https://github.com/weareinteractive/ansible-apt)

## License

This project is under the MIT License. See the [LICENSE](https://sbaerlo.ch/licence) file for the full license text.

## Copyright

(c) 2019, Arillso
