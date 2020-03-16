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

# URL needed to check Kibana status and/or apply configs via the API (NGINX is installed by default so you can ommit the port number, port 80 is used by default)
kibana_url: "http://kibana.example.local"
```

* `FILE: {{ playbook_dir }}/vars/kibana-secrets-production.yml`

```
# Credentials that allow Kibana to access system indices in Elasticsearch (.kibana)
kibana_es_user: kibana
kibana_es_password: <PASSWORD_FOR_KIBANA_BUILT_IN_USER>
# Since all users are configured during Elasticsearch setup, you can refer to the corresponding password in the Elasticsearch vars file
kibana_es_password: "{{ elasticsearch_built_in_users['kibana']['password'] }}"
# This key is a must if you have multiple Kibana instances behind a load balancer
xpack_security_encryption_key: <STRONG_ENCRYPTION_KEY>
```
