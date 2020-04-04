# Ubuntu 18.04 LTS desktop box (setup using Vagrant + Ansible)

Based on [original repo](https://github.com/heidemn/vagrant-bionic-desktop)

- **VirtualBox version 6.0.10**

## Customize

If you aren't using VirtualBox, or if you're fine with the default disk size of 10 GB:

- Skip the plugin installation.
- Remove the `config.disksize...` line from the Vagrantfile.

## How to run it

```
vagrant up
```

- You may be prompted for plugin installation. It will automatically install Guest Additions and enable Vagrant disk size configuration. When plugins are installe simply repeat command `vagrant up`.

- After succesfull setup, reload VM and start your work.

```
vagrant reload
```

After the reboot, the VM screen should show the LightDM login screen.
Log in as user "vagrant", password "vagrant".

Re-running the provisioners:

```
# When VM is running:
vagrant provision

# When VM is powered off:
vagrant up --provision 2>&1 | tee log.txt
```
