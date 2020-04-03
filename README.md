# vagrant-ubuntu-desktop

Ubuntu 18.04 LTS desktop box (setup using Vagrant + Ansible)

Based on [original repo](https://github.com/heidemn/vagrant-bionic-desktop)

VirtualBox version 6.0.10

## Customize

If you aren't using VirtualBox, or if you're fine with the default disk size of 10 GB:

- Skip the plugin installation.
- Remove the `config.disksize...` line from the Vagrantfile.


## How to run it

```
vagrant up

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
