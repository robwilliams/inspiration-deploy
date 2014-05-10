## Setup

Create an inventory file for the environment you need. A symlink is provided
for the vagrant generated inventory called `hosts-development`.

e.g. `hosts-production`

```
app1 ansible_ssh_host=152.183.164.25

[app]
app1
```

## Usage

### Bootstrap

`ansible-playbook -i hosts-production -u root bootstrap.yml`

After running the bootstrap playbook for the first time, 'root' can no longer 
be used to connect via ssh for security reasons. 

The bootstrap playbook sets up a deploy user with sudo rights which we can use instead.

`ansible-playbook -i hosts-production -u deploy --sudo --ask-sudo-pass bootstrap.yml`

The vagrant user on the development box is not disabled and can still be used.

`vagrant up` or `vagrant provision`

### Provisioning

## Things to watch out for

If you rebuild a box on the same ip then expect ssh to fail.
Clean out the related entry in `~/.ssh/known_hosts` to stop this.
