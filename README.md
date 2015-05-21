#Vertica
Installs [Vertica](http://www.vertica.com/) either standalone or part of a cluster.

Tested with Vertica 7.x

##Requirements
- vertica_ssh_key_location - location of where to create and place ssh keys for dbadmin
- vertica_dbadmin_password - password to be used for dbadmin on the database mon

##Optional parameters
If the variables `vertica_cluster` and `vertica_group` are both defined the nodes will be setup to be in a cluster. 

vertica_cluster is a common separated list of the group of nodes that you want to be apart of your cluster and vertica_group
is set to that group from the ansible inventory file.

See the example playbook below.

If defined with a valid license the contents of `vertica_license_key` will be used for the license key.

## Other notes
Vertica recommends setting the kernel disk scheduling algorithm to deadline. This can be done by adding the kernel bootparam "elevator=deadline" then
restarting. This optimization is not done by the role.

This role does not create the database. That creation is in the role [Monasca-schema](https://github.com/hpcloud-mon/ansible-monasca-schema)

##Example Playbook

    hosts: vertica
    sudo: yes
    roles:
      - {role: vertica, 
         vertica_group="{{groups['vertica']}}", 
         vertica_cluster="10.10.10.1,10.10.10.2,10.10.10.3",
         tags: [vertica]}

##License
Apache

##Author Information
Michael Hoppal and Tim Kuhlman
Monasca Team email monasca@lists.launchpad.net

