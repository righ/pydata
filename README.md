# Requirements
* Vagrant >= 1.7.4
* Ansible >= 1.8.4
* VirtualBox >= 5.0.6

# Usage
## Setup
```sh
$ vagrant up
$ vagrant provision
# or the following (Windows Cygwin and so on)
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
As you log in, you will be automatically moved to `~/data/` directory.

### Start up jupyter notebook
Execute the following on guest(virtual) environment.
```sh
$ jupyter notebook --ip=* --port=8888
```

When finished, try to access: http://192.168.35.125:8888/

You can access from host environment.

If you would like to share the window with other people,
please remove comment-out of Vagrantfile (near #L33).
And, please ask them to access `http://[your ip]:8888/`.

```ruby
  config.vm.network "forwarded_port", guest: 8888, host: 8888
```


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

## Available libraries
The following libraries work in python3.

* jupyter
* numpy
* matplotlib
* pandas
* sympy
* scipy
* numba
* cython
* numba
* pil

# History
## 2016-03-19
* Python3

## 2016-03-18
* Updated readme
* Added `numba` and `cython` installation.

## 2016-03-17
* Initial commit


# future support
* OpenCV3
