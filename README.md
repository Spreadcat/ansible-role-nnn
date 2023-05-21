# Role dbv.nnn

Ansible role to install and configure a the [nnn][#nnn] file manager.

## Requirements

* The NNN package must be available in the local file repository.
* Rsync

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
nnn_path_environment_file: str
```

* Path for the file to define the export for the plugin inclusion in.

  ```yaml
  # Example:
  nnn_path_environment_file: "{{ lookup('env', 'HOME') }}/.bashrc"
  ```

```yaml
nnn_plugins_install: bool
```

* If set to true plugins will be fetched from `nnn_url_master` and installed into the plugin directory.

  ```yaml
  # Example:
  nnn_plugins_install: true
  ```

```yaml
nnn_plugins_update: bool
```

* If set to true, existing plugins will be overwritten from the github
  source and updated on the local disk.

  ```yaml
  # Example:
  nnn_plugins_update: true
  ```

## Configuration variables

```yaml
nnn_archmnt: str
```

* Achive mounter for NNN.

  ```yaml
  # Example:
  nnn_archmnt: "fuse-archive"
  ```

```yaml
nnn_order: list
```

* Set directory specific ordering.

  ```yaml
  # Example:
  NNN_ORDER:
    - key: t
      path: /var/log
  ```

```yaml
nnn_plug: list
```

* List of plugins to install/enable.

  ```yaml
  # Example:
  nnn_plugins:
    - key: i
      plugin: imgview
    - key: j
      plugin: imgresize
  ```

## Other variables

```yaml
nnn_group: str
```

* Default group for NNN.

  ```yaml
  # Example:
  nnn_group: jdoe
  ```

```yaml
nnn_owner: str
```

* Default user for NNN.

  ```yaml
  # Example:
  nnn_owner: jdoe
  ```

```yaml
nnn_packages: list
```

* defaults file for nnn Default packages to install for NNN

  ```yaml
  # Example:
  nnn_packages:
    - nnn
  ```

```yaml
nnn_packages_state: str
```

* Default state for the installed packages.

  ```yaml
  # Example:
  nnn_packages_state: "present"
  ```

```yaml
nnn_path_config_dir: str
```

* Default path to the configuration directory.

  ```yaml
  # Example:
  nnn_path_config_dir: "/home/user/.config/nnn"
  ```

```yaml
nnn_url_master: str
```

* URL for downloading a compressed version of the source code for nnn. This is used to fetch the plugins and install them when required.

  ```yaml
  # Example:
  nnn_url_master: "https://github.com/jarun/nnn/archive/master.tar.gz"
  ```

## Dependencies

* None

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- hosts: all
  roles:
     - role: dbv.nnn
```

## Limitations

The role lacks support for most of the environment variables of nnn at this point. This is due to the role growing as I need it and which parameters I need to set. But I put some effort into making it easy to extend when needed.
If you miss a particular parameter, just pop me a message.

## License

MIT

## Author Information

* This role is written an maintained by DBV.

[#nnn]: https://github.com/jarun/nnn
