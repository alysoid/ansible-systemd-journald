# [Catena](https://github.com/alysoid/catena) Ansible Role: systemd-journald

Manage [systemd-journald](https://man.archlinux.org/man/systemd-journald.8.en), a system service that collects and stores logging data. It creates and maintains structured, indexed journals based on logging information that is received from a variety of sources: kernel (kmsg), system logs, stdout and stderr of service unit, audit records.

## Role default variables

| Variable                  | Default | Info                                                                        |
| ------------------------- | ------- | --------------------------------------------------------------------------- |
| `catena_journald`         | `[]`    | Set configuration files that control systemd-journal.                       |
| `catena_journald_cleanup` | `no`    | Remove existing configuration files: `/etc/systemd/journald.conf.d/*.conf`. |

### `catena_journald`

Manage [journald.conf.d - Journal service configuration files](https://man.archlinux.org/man/journald.conf.5.en).

Configuration files will have the .conf extension and will be placed in the configuration snippets directory `/etc/systemd/journald.conf.d`.

```yaml
# Default
catena_journald: []

# Example
catena_journald:
  # /etc/systemd/journald.conf.d/main.conf
  - name: main
    options:
      Storage: persistent
      SystemMaxUse: 100M
      SystemMaxFilesize: 100M
      SystemKeepFree: 50M
```
