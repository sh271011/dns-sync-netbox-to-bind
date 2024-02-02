# Ansible Role: bind-2-netbox-sync

### Description

This Ansible role sets up DNS synchronization between BIND and NetBox using OctoDNS.

### Requirements

- Ansible 2.9 or later
- Python 3.x

### Role Variables

Role variables are defined in vars/main.yml, replace below variables as per your environment.

```bash
bind_directory_path: "remote server bind directory path"
netbox_url: "netbox url"
netbox_api_token: "netbox_api_token"
dns-sync-directory: "directory where you want venv to be created"
```
At Play Level we have below variable.

- `target_bind_server`: (Required) The target BIND server for synchronization.
Example:

### Templates

The role uses the following templates.

- **config.j2** , for generating the **config.yaml** file for Octodns
- **requirements.txt**, file specifying the python dependencies
- **__init__.py** , to update octodns_netbox plugin to work with docker installation of netbox

### Example Playbook

```yaml
- name: NetBox to BIND DNS Sync
  hosts: bind_server #your target bind server goes here
  become: true
  roles:
    - dns_sync

```

### Usage
1. Install ansible
   
```bash
pip install ansible
```

2. Create an inventory file with your BIND server:
```bash
[bind_servers]
your_bind_server ansible_host=your_bind_server_ip
```

3. Create a playbook (dns-sync.yml) with the example playbook content.

4. Run the playbook:

```bash
ansible-playbook -i inventory.ini dns-sync.yml
```


### Author Information
- Author: Shoaib Mohammed Shahapuri
- Contact: ShoaibMohammed.Shahapuri@wwt.com