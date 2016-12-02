# Requirements
* Vagrant >= 1.8.5
* Ansible >= 1.8.4
* VirtualBox >= 5.0.14

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
please remove comment-out of Vagrantfile (near #L33) and restart vagrant.

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

## Config
Part of config items have cut out to "config.rb".
If you want to modify config, then please rewrite the file.

## Available libraries
The following libraries work in python3.

* jupyter
* numpy
* matplotlib
* pandas
* sympy
* scipy
* cython
* numba
* pil
* tensorflow

## About tensorflow
### Documents
* https://github.com/tensorflow/tensorflow

### Study tensorflow
```sh
$ git clone https://github.com/tensorflow/tensorflow.git ~/data/tensorflow
$ cd ~/data/tensorflow/tensorflow/examples
# if another session already exists on the same port, execute this command, after closing existing session.
$ jupyter notebook --ip=* --port=8888
```

#### tutorial
* http://192.168.35.125:8888/notebooks/tutorials/deepdream/deepdream.ipynb

#### udacity
* http://192.168.35.125:8888/notebooks/udacity/1_notmnist.ipynb
* http://192.168.35.125:8888/notebooks/udacity/2_fullyconnected.ipynb
* http://192.168.35.125:8888/notebooks/udacity/3_regularization.ipynb
* http://192.168.35.125:8888/notebooks/udacity/4_convolutions.ipynb
* http://192.168.35.125:8888/notebooks/udacity/5_word2vec.ipynb
* http://192.168.35.125:8888/notebooks/udacity/6_lstm.ipynb

# History
## 2016-12-02
* Fixed bug for vagrant "1.8.7".
* Added config items.
* Cut out config items to "config.rb".

## 2016-11-30
* Upgrade ubuntu version from 14.04 to 16.04
  * Libraries installation has been migrated to pip.

## 2016-03-30
* Added `tensorflow` installation.

## 2016-03-19
* Suppoted Python3.
* Unsupported Python2.

## 2016-03-18
* Updated readme
* Added `numba` and `cython` installation.

## 2016-03-17
* Initial commit


# future support
* OpenCV3
