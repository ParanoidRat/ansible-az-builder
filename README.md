# Ansible Role :: Azure Builder
This repository contains Ansible role for deployment of resources into Azure. Relies on the `az` Azure CLI tool being present as well as some common task
modules from [ParanoidRat/ansible-common-tasks][1].

## Getting Started
1.  Download repo into the folder with roles
```bash
git clone https://github.com/ParanoidRat/ansible-az-builder.git roles/az-builder
```

2.  Use role in a playbook
```yaml
- name: "Deploy to Azure :: Docker"
  hosts: az-builder
  run_once: yes
  tags:
    - role::az-builder
  roles:
    # Deploy `az_builder_deployments` to Azure using `az-builder` host
    - az-builder
```

## Parameters

Deployments are described as follows:
```yaml
az_builder_deployments:
  - name: "Cisco-CSR-1000V"
    url: https://github.com/Azure/azure-quickstart-templates/blob/master/cisco-csr-1000v/azuredeploy.json
    params: azuredeploy.parameters.cisco-csr-1000v.json
    subscriptionId: af95b82a-3fbf-45fd-b6bd-b6c62ea8b5b4
    location: West Europe
    resgroup: DEV-VPN
```
-   `name` - name of the deployment in Azure
-   `url` - URL where ARM template resides
-   `params` - full path to local file with deployment parameters
-   `subscriptionId` - Azure subscription to deploy resources to
-   `location` - Location of deployed resources
-   `resgroup` - Resource Group of deployed resources (will be created, if non-existent)

Debug output could be enabled with parameter `az_builder_debug: yes`


## Requirements
*   Ansible 2.4

## Tested On
*   CentOS 7.3
*   Ubuntu 16.04 LTS

## Authors
*   [ParanoidRat][2]

## License
The work is licensed under the CC-BY-SA 4.0 License. Unless otherwise stated, modifications are also licensed under the CC-BY-SA 4.0 License. See the [LICENSE.md](LICENSE.md) file for details and specific licensing of the modifications.

You should have received a copy of the license along with this work (see the [CC-BY-SA-4.txt](CC-BY-SA-4.txt) file for details). If not, see [here][3].

[1]: https://github.com/ParanoidRat/ansible-common-tasks
[2]: https://github.com/ParanoidRat
[3]: https://creativecommons.org/licenses/by-sa/4.0/legalcode
