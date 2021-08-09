# vagrant-boiletplate

This is a boilerplate for a standard Vettabase Vagrantfile.


## Configuration

When creating the Vagrant machine, it is possible to configure the resulting box
by editing the configuration file. To avoid setting a property in the
configuration file, just leave it blank. Don't delete any key from the file.

The default configuration file is `config.yaml`. It is possible to use a different
file by setting the `CONFIG` configuration variable.

Each setting in the configuration file can be overridden with an environment
variable.

Settings that are not set in the configuration file nor using environment
variables will use the default values hardcoded in the Vagrantfile.

Environment variables can be passed in this way:

```
VAR1=VALUE1 VAR2=VALUE2 vagrant up
```


### Generic settings

These are the generic settings.

| Config File       | Environment       | Default              | Description |
| ----------------- | ----------------- | -------------------- | ----------- |
| `box`             | `BOX`             | `'ubuntu/bionic64'`  | The name of the base box (the VM operating system).
| `provider`        | `PROVIDER`        | `'virtualbox'`       | The Vagrant provider to use, case-insensitive.


### Provider options

Some settings are passed to the providers that support them, to determine the
characteristics of the guest system.

* YAML dictionary: `vm`
* Variables prefix: `VM_`

| Config File  | Environment  | Default        | Description |
| ------------ | ------------ | -------------- | ----------- |
| `vm.name`    | `VM_NAME`    | `''`           | Name of the VM, used by the provider.
| `vm.description` | `VM_DESC` | `''`          | Human-readable description of the VM, used by the provider.
| `vm.hotplug` | `VM_HOTPLUG` | `'on'`         | Wether hotplug should be ON or OFF for the VM.
| `vm.cpu`     | `VM_CPU`     | `2`            | Number of vCPU's in the VM.
| `vm.ram`     | `VM_RAM`     | `4096`     | Amount of RAM in M.

### Private networking

To add the guest system to a private network (if the provider supports this),
use these settings.

* YAML dictionary: `private_network`
* Variables prefix: `PNET_`

| Config File | Environment | Default | Description |
| ----------- | ----------- | ------- | ----------- |
| `private_network.enable` | `PNET_ENABLE` | `'NO'` | Set to 'YES' (case insensitive) to enable private networking.
| `private_network.name`   | `PNET_NAME`   | `''`   | Useful if you use multiple private networks.
| `private_network.ip`     | `PNET_IP`     | `''`   | Specify an IP (version 4 or 6), or leave blank to automatically assign one via DHCP.

### Synced Folders

To setup synced folders, set the `synced_folders` property in the configuration file.
Currently, no environment variable can overwrite it.

`synced_folders` is an array. Here's an example of how to populate it:

```
synced_folders:
  - { host: '.', guest: '/Vagrant' }
```

By default, no synced folder is created.

### Guest system

These settings affect the configuration of the guest system.

* YAML dictionary: `guest_system`
* Variables prefix: `SYS_`

| Config File                | Environment       | Default | Description |
| -------------------------- | ----------------- | ------- | ----------- |
| `guest_system.swappiness`  | `SYS_SWAPPINESS`  | `1`     | Linux swappiness


## Usage

...


## Copyright and Contacts

This repository is distributed under the terms of the GNU AGPL, version 3. Copyright: Vettabase Ltd.

To contact us:

- info@vettabase.com
- https://vettabase.com

