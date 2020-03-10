Ansible-Kibana
=========

#### It is highly recommended that you do not directly access this repository from your CI/CD jobs. Make a fork in your project's SCM instead. By doing so, you make sure that your cluster will not be broken in case one of the new commits appear to have a bug. You can keep the fork synchronized with the origin manually

#### See https://github.com/arsenii-stefanov/ansible-elasticsearch-cluster for a playbook example and complete Elasticsearch installation guide

### Config Example

* `FILE: {{ playbook_dir }}/vars/kibana-production.yml`

```
kibana_installation_type: "docker"        # Available options: docker

kibana_main_mount_dir: "/srv"

# KIBANA CONFIG
kibana_image_name: "docker.elastic.co/kibana/kibana"
kibana_image_tag: "7.3.2"
kibana_max_old_space_size: "4096"

# NGINX CONFIG
kibana_dns_names: [ "kibana.example.local" ]

kibana_url: "http://kibana.example.local"
```

* `FILE: {{ playbook_dir }}/vars/kibana-secrets-production.yml`

#### This file is optional, these variables are only needed in case you desire to execute Kibana post installation tasks by defining one of the following variables: 'kibana_config_files' or 'kibana_config_templates'

```
kibana_es_user: elastic
kibana_es_password: <THE_PASSWORD_YOU_USED_DURING_ELASTICSEARCH_SETUP>
```
