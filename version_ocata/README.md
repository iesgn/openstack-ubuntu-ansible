openstack-ubuntu-ansible
========================

Ansible playbooks for installing *OpenStack Ocata* on Ubuntu Xenial (16.04)

These playbooks have been written in the hope of using them in a real deployment
with physical servers, but thay can be used too to deploy a OpenStack test
environment terraform on OpenStack (see https://github.com/iesgn/terraform-openstack)

**This is still a work in progress**

## Software used (specific versions):

- Ubuntu 16.04 LTS
- Linux kernel: 4.4.0
- Open vSwitch: 2.6.1
- OpenStack: Ocata
- Ansible: 2.3

## OpenStack componens included:

Keystone, Glance, Nova (KVM/Qemu), Neutron (OVS) and Cinder (LVM+iSCSI)

## Deployment schema


[Per tenant router with private networks](http://docs.openstack.org/havana/install-guide/install/apt/content/section_networking-routers-with-private-networks.html)

## Configuration

![schema](https://raw.githubusercontent.com/iesgn/openstack-debian-ansible/master/img/openstack-debian-ansible.png)

The file *groups_var/all* contains all variables needed by ansible playbooks and
they can be customized if needed. It's **mandatory** to define the following
variables according to your LAN:

    controller_external_ip: 192.168.1.101
    storage_external_ip: 192.168.1.101
    network_node_external_ip: 192.168.1.101
    network_node_external_netmask: 255.255.255.0
    network_node_external_CIDR: 24
    external_gateway: 192.168.1.1

## Run ansible playbooks to configure the cloud

    ansible-playbook site.yml --sudo

## Using OpenStack

Open your browser and type in the notification bar http://192.168.1.101 or the corresponding external IP chosen.

## References

This work was inspired, but not based on, these previous projects (not updated) to deploy former OpenStack releases on Ubuntu:

- [https://github.com/openstack-ansible](https://github.com/openstack-ansible)
- [https://github.com/djoreilly/quantum-ansible](https://github.com/djoreilly/quantum-ansible)
