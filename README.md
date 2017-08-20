## ansible-openstack-env-creator

A tool to create and populate an OpenStack project.

Specifically it will:
- Create a new OpenStack project.
- Create Security Groups
- Create and add keypair(s)
- Create and boot VMs
- Create a local stackrc file for to aid in administrating the project.


## usage

1. Generate vars with the ansible-openstack-env-template tool.
2. Add vars to your own ansible-openstack-env-vars repository
3. Install python modules `pip install -r ./requirements.txt`
4. Run deployment tool and specify environment being deployed. `./bin/deploy -e qa01 -a "-vv --check"`


## destroy an existing project

```
ansible-playbook -i ../ansible-openstack-env-vars/<ENV_NAME> playbooks/destroy_project.yml -vv
```

The preceeding command will apply the following ONLY to the supplied env name:
- Remove all `known_hosts` entries from your localhost for a given OpenStack project specified.
- Remove the specified projects local keypairs and stackrc files.
- Remove the specified projects keypairs from the OpenStack cluster.
- Remove the specified projects VMs and associated floating ips(if there are any).
- Lastly it will also remove the project from the OpenStack cluster.
