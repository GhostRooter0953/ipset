# ipset

The role installs and configure ipset

## Usage (examples)

### Minimal

```yaml
    - role: ipset
```

### Cloudflare + custom lists

```yaml
    - role: ipset
      lists:
        - {name: cf-v4, family: inet}
        - {name: cf-v6, family: inet6}
```

### Custom ipset lists with list of IP

```yaml
- role: ipset
  update_lists: false
  lists:
    - name: custom-v4
      family: inet
      ips:
        - 123.123.123.123
        - 234.234.234.234
    - name: custom-v6
      family: inet6
      ips:
        - 2001:19f0:210:125d::436
        - 2607:fcd0:bb70:1e00::4020
```

## Available parameters

### Main

| Param | Default | Description |
| -------- | -------- | -------- |
| `ipset_setup` | `full` | Setup mode |
| `ipset_default_lists` | See next header. | Default ipset lists |
| `lists` | `[]` | Custom ipset lists |

### List parameters

By default the role installs 4 ipset lists:

```yaml
ipset_default_lists:
  - {name: v4, family: inet}
  - {name: v6, family: inet6}
```

Additonal lists can be enabled using these parameters:

| Param | Default | Description |
| -------- | -------- | -------- |
| `name` | - | name of an ipset list, any name, e.g. `client-ssh` |
| `family` | - | family of an ipset list, `inet` or `inet6` |
| `uri` | - | url which contains a list of IPs for a specific ipset list |
| `ips` | - | list of IP adresses for list |

## TODO

- improve check mode support. Some task disabled for check mode
- delete update_lists param
