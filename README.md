Description
===========

This is an OpenStack HEAT template to deploy [Magento](http://magento.com/) 
to multiple servers in an OpenStack cloud. Currently, only Magento 1.9.0.1 is
supported.

This template uses the following salt formulas:
* [sync-formula](https://github.com/rcbops/sync-formula)
* [mysql-formula](https://github.com/rcbops/mysql-formula)
* [magento-formula](https://github.com/rcbops/magento-formula)

This template deploys:
* a private network
* a salt-master
* a database (minion)
* a variable number of web servers (minions)(also specified at stack creation)
* an haproxy node for the web servers (minion)

For access to nodes in the magento cluster, a floating ip will be assigned to the 
salt-master. Another floating ip will be assigned to the haproxy node.

Requirements
============
* A Heat provider that supports the following:
  * OS::Neutron::Net
  * OS::Neutron::Subnet
  * OS::Neutron::Router
  * OS::Neutron::RouterInterface
  * OS::Neutron::FloatingIP
  * OS::Neutron::FloatingIPAssociation
  * OS::Neutron::Port
  * OS::Heat::SoftwareConfig
  * OS::Heat::SoftwareDeployment
  * OS::Heat::RandomString
  * OS::Heat::ResourceGroup
  * OS::Nova::Server
  * OS::Nova::KeyPair

* An Ubuntu image (12.04 or newer) preconfigured with heat-cfntools and heat config-script. 
Instructions for creating a heat-cfntools enabled image for use with Heat can be 
found [here] (http://docs.openstack.org/developer/heat/getting_started/jeos_building.html).

* An OpenStack username, password, and tenant id.
* [python-heatclient](https://github.com/openstack/python-heatclient)
`>= v0.2.12`:

```bash
pip install python-heatclient
```

License
=======
```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
