Role Name
=========

Install kong with cassandra

Role Variables
--------------

```yaml
# Install cassandra node for kong
kong_cassandra_node: yes

# Cassandra version
kong_cassandra_version: 2.1.12

# Java install root
kong_cassandra_java_path: /opt/java

kong_source_ver: "0.7.0"
kong_source_deb: "https://github.com/Mashape/kong/releases/download/{{ kong_source_ver }}/kong-{{ kong_source_ver }}.{{ ubuntu_flavor }}_all.deb"

# where to download kong and java packages
kong_download_dir: "/opt"

kong_service_state: "started"
kong_service_enabled: yes

kong_dependencies:
  - netcat
  - lua5.1
  - openssl
  - libpcre3
  - dnsmasq

kong_user: "kong"
kong_group: "{{ kong_user }}"
kong_conf_dest: "/etc/kong/kong.yml"
kong_service_log_dir: "/var/log/kong"
kong_service_pid: "/usr/local/kong/nginx.pid"
```


Example Playbook
----------------

```yaml
# install kong with cassandra
- hosts: all
  roles:
    - kong

# install without cassandra
- hosts: all
  vars:
    kong_cassandra_node: no
  roles:
    - kong
```

License
-------

MIT
