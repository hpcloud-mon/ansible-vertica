#Vertica
Installs Vertica [Vertica](http://www.vertica.com/) either standalone or part of a cluster.

Tested with Vertica 7.x

##Requirements

##Optional parameters
If the variable `vertica_cluster` is defined the nodes will be setup to be in a cluster. Valid definition of the variable is a list of the nodes and can
easily be set if using a group for your Vertica cluster, see the example playbook below.

If defined with a valid license the contents of `vertica_license` will be used for the license key.

## Other notes
Vertica recommends setting the kernel disk scheduling algorithm to deadline. This can be done by adding the kernel bootparam "elevator=deadline" then
restarting. This optimization is not done by the role.

##Example Playbook

    hosts: vertica
    sudo: yes
    roles:
      - {role: vertica, vertica_cluster="{{groups['vertica']}}", tags: [vertica]}

##License
Apache

##Author Information
Michael Hoppal and Tim Kuhlman
Monasca Team email monasca@lists.launchpad.net
