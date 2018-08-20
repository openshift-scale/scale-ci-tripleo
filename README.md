# tripleo-quickstart-scalelab

Playbook to deploy Tripleo OpenStack on ScaleLab for OpenShift on OpenStack performance and scale testing.

## Deploying Undercloud and Overcloud

From CLI

```
$ cp hosts.example hosts
$ # Add Undercloud host to hosts
$ # Edit vars in vars/deploy.yml or define Environment vars
$ ansible-playbook -i hosts deploy-scalelab.yaml
```

If using environment variables (Ex Jenkins Job Parameters), define the following:

```
#
# Ansible SSH Vars
#
PUBLIC_KEY
PRIVATE_KEY
#
# OpenStack Version/Build Variables:
#
OSP_RHOS_RELEASE_URL
OSP_RHOS_VERSION
OSP_RHOS_RHEL_VERSION
OSP_RHOS_RELEASE_VERSION
OSP_RHOS_BUILD
OSP_INSECURE_REGISTRY
OSP_CEPH_INSECURE_REGISTRY
OSP_CONTAINER_NAMESPACE
OSP_CONTAINER_TAG
OSP_CONTAINER_CEPH_NAMESPACE
OSP_CONTAINER_CEPH_IMAGE
OSP_CONTAINER_CEPH_TAG
#
# Undercloud Variables:
#
OSP_CLUSTER_ID
OSP_REBUILD_UNDERCLOUD
OSP_UNDERCLOUD_HOSTNAME
OSP_QUADS_TICKET_NUMBER
OSP_QUADS_FOREMAN_URL
OSP_STACK_PASSWORD
OSP_INSTACKENV_NO_INTROSPECTION
OSP_NODE_PROVIDE_TIMEOUT
OSP_INTROSPECTION
OSP_BULK_INTROSPECTION_TIMEOUT
OSP_INTROSPECTION_SCRIPT
OSP_NODE_CLEANING
#
# Overcloud Variables
#
OSP_INSTACKENV_JSON
OSP_FIREWALL_DRIVER
OSP_CONTROLLER_TYPE
OSP_CEPHSTORAGE_TYPE
OSP_COMPUTE_TYPE
OSP_NUM_CONTROLLERS
OSP_NUM_CEPHSTORAGE
OSP_NUM_COMPUTE
OSP_CEPH_POOL_VM_PG_NUM
OSP_CEPH_POOL_IMAGES_PG_NUM
OSP_CEPH_POOL_VOLUMES_PG_NUM
#
# Undercloud and Overcloud Network Setup:
#
OSP_UNDERCLOUD_LOCAL_INTERFACE
OSP_NTP_SERVER
OSP_EXTERNAL_NETWORK_SETUP
OSP_DNS_SERVER
OSP_EXTERNAL_VLAN
OSP_EXTERNAL_NET_POOL_START
OSP_EXTERNAL_NET_POOL_END
OSP_EXTERNAL_NET_GATEWAY
OSP_EXTERNAL_NET_CIDR
OSP_EXTERNAL_NETWORK_VIP
OSP_FIP_POOL_START
OSP_FIP_POOL_END
OSP_UNDERCLOUD_PUBLIC_INTERFACE
OSP_UNDERCLOUD_PRIVATE_EXTERNAL_INTERFACE
OSP_PRIVATE_EXTERNAL_ADDRESS
OSP_PRIVATE_EXTERNAL_NETMASK
```

## Install Browbeat Monitoring

From CLI

```
$ cp hosts.example hosts
$ # Add Undercloud host to hosts
$ # Edit vars in vars/browbeat.yml or define Environment vars
$ ansible-playbook -i hosts install-browbeat.yaml
```

If as a Jenkins Job, define the following parameters:

```
OSP_CLUSTER_ID
BROWBEAT_DNS_SERVER
BROWBEAT_GRAPHITE_HOST
BROWBEAT_GRAPHITE_PREFIX
BROWBEAT_GRAFANA_HOST
BROWBEAT_GRAFANA_APIKEY
BROWBEAT_COLLECTD_COMPUTE
BROWBEAT_COLLECTD_RABBITMQ
BROWBEAT_COLLECTD_CEPH
```

## Updating User on Cluster

From CLI

```
$ cp hosts.example hosts
$ # Add Undercloud host to hosts
$ # Edit vars in vars/update-users.yml or define Environment vars
$ ansible-playbook -i hosts update-users.yaml
```

If as a Jenkins Job, define the following parameters:

```
OCP_ON_OSP_CLUSTER_ID
OCP_ON_OSP_USER
OCP_ON_OSP_EMAIL
```
