##  VNF Onboarding Application Blueprint

This blueprint deploys to Openstack a VM running VNF Onboarding application inside a Docker container.


## prerequisites

You will need a *Cloudify Manager* running in Openstack. The Cloudify manager should be setup using the [Cloudify environment setup](https://github.com/cloudify-examples/cloudify-environment-setup) - that's how we test this blueprint. The following are therefore assumed:
* You have uploaded all of the required plugins to your manager in order to use this blueprint. (See the imports section of the blueprint.yaml file to check that you are using the correct plugins and their respective versions.)
* You have created all of the required secrets on your manager in order to use this blueprint. (See #secrets.)


#### Secrets

The following secrets are expecting in your Openstack Cloudify Manager:

  * agent_key_private
  * agent_key_public
  * external_network_name: This is the network on your Openstack that represents the internet gateway network.
  * public_network_name: An openstack network. (Inbound is expected, outbound is required.)
  * public_subnet_name: A subnet on the public network.
  * private_network_name: An openstack network. (Inbound is not expected, outbound is required.)
  * private_subnet_name: A subnet on the network. (Inbound is not expected, outbound is required.)
  * router_name: This is a router that is attached to your Subnets designated in the secrets public_subnet_name and private_subnet_name.
  * region: Your Keystone V2 region.
  * keystone_url: Your Keystone V2 auth URL.
  * keystone_tenant_name: Your Keystone V2 tenant name.
  * keystone_password: Your Keystone V2 password.
  * keystone_username:Your Keystone V2 username.


### Step 1: Install the VNF Onboarding Application.

```shell
$ cfy install \
    https://github.com/cloudify-examples/vnf-onboarding-blueprint/archive/master.zip \
    -b vnf-onboarding-app \
    -n openstack-blueprint.yaml
```
