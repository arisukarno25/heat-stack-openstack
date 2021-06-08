# heat-stack-openstack

## What is Heat Stack Openstack?
Heat is the main project in the OpenStack Orchestration program. It implements an orchestration engine to launch multiple composite cloud applications based on templates in the form of text files that can be treated like code. A native Heat template format is evolving, but Heat also endeavours to provide compatibility with the AWS CloudFormation template format, so that many existing CloudFormation templates can be launched on OpenStack. Heat provides both an OpenStack-native ReST API and a CloudFormation-compatible Query API. (source: https://wiki.openstack.org/wiki/Heat)

## Configuration
- name: heat-instance-XX
- image: cirros-XX (use the existing one)
- flavor: heat-flavor-XX
- keypair: heat-key-XX
- network: heat-network-XX
- security group: heat-sg-XX
- floating ip: from external-net-XX

## How to run?
- Clone repository 

```
git clone https://github.com/arisukarno25/heat-stack-openstack.git
cd heat-stack-openstack
```

- Edit mystack-6.yml

```
parameters:
 demo_net_name: heat-network-6
 demo_net_cidr: 172.28.6.0/24
 demo_net_gateway: 172.28.6.1
 demo_net_pool_start: 172.28.6.10
 demo_net_pool_end: 172.28.6.254
 demo_subnet_name: heat-subnet-6
 demo_ext_net_name: external-net-6
 demo_router_name: heat-router-6
 demo_sg_name: heat-sg-6
 demo_key_name: heat-key-6
 demo_public_key: <your ssh key>
 demo_image_name: cirros-6
 demo_flavor_name: heat-flavor-6
 demo_server1_name: heat-instance-6
```

- Create stack

```
openstack stack create -e mysack-env-6.yml -t mystack-6.yml mystack
```
