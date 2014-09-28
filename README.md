Install Openstack With Vagrant And Ansible
==========================================

We can use vagrant provison feature with ansible install openstack in vagrant simply.

## How to run it

### Requirements

* Install Vagrnat in your local.
* Install Ansible in your local.
* Get the base vagrant box from this [ubuntu/trusty64](https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box)

For linux/Mac user

```
pip install ansible
```

```
vagrant box add ubuntu/trusty64 https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box
```

```
git clone git@github.com:yunlzheng/ansible-openstack.git
```

```
vagrant up --provision
```

### Default openstack environment

* controller 10.1.0.11(1 processor, memery 1 GB)
* network 10.1.0.12(1 processor, memery 512 MB)
* compute1 10.1.0.13(1 processor, memory 2 GB)

## How to use it

After provision without error. You can visit your openstack dashbord with address [http://10.1.0.11/horizon](http://10.1.0.11/horizon)

> Note: In this automate script we use controller as host name. If you want visit the VNC. you need add the follow line in your host machine /etc/hosts.
> 10.1.0.11   controller
