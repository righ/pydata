# Requirements
* Vagrant >= 1.7.4
* Ansible >= 1.9.3
* VirtualBox >= 5.0.6

# Usage
## Setup
```sh
$ vagrant up
$ vagrant provision
# or the following (windows Cygwin and so on)
$ ansible-playbook -i inventory/vagrant provision.yml
```

The following directories are shared between host and guest.
* `pydata/data/` (host) <-> `~/data/` (guest)
* `pydata/` (host) <-> `/vagrant/` (guest)

## Start
### Login guest environment
```sh
$ vagrant ssh
```
When you log in, you will be automatically moved to `~/data/` directory.

### Start up jupyter notebook
Execute the following on guest(virtual) environment.
```sh
$ jupyter notebook --ip=* --port=8888
```

And, try to access: http://192.168.35.125:8888/

You can access from host environment or machine on the same network.

## Shutdown
```sh
$ vagrant halt
```

## Restart
```sh
$ vagrant reload
```

## Delete
```sh
$ vagrant destroy # -f
```

## Update environment
```sh
$ git pull
$ vagrant up --provision # or vagrant provision
```

## History
### 2016-03-17
* initial commit
