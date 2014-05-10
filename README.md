# Usage

## Bootstrap

```ansible-playbook -i hosts-production -u root bootstrap.yml```

After running the bootstrap playbook for the first time, 'root' can no longer 
be used to connect via ssh for security reasons. 

The bootstrap playbook sets up a deploy user with sudo rights which we can use instead.

```ansible-playbook -i hosts-production -u deploy --sudo --ask-sudo-pass bootstrap.yml```

The vagrant user on the development box is not disabled and can still be used.

```vagrant up``` or ```vagrant provision```
