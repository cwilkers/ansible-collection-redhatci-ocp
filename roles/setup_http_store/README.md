# Setup HTTP Store

Sets up a web host which can be used to distribute ISO's for `boot_iso` role

## Role Variables

| Variable                  | Required | Default                                            | Comments                                                                                                                             |
| ------------------------- | -------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| http_store_container_name | no       | http_store                                         |                                                                                                                                      |
| http_store_pod_name       | no       | http_store_pod                                     |                                                                                                                                      |
| http_dir                  | no       | /opt/http_store                                    |                                                                                                                                      |
| http_data_dir             | no       | "{{ http_dir }}/data"                              |                                                                                                                                      |
| container_image           | no       | registry.centos.org/centos/httpd-24-centos7:latest | If you change this to anything other than the same image on a different host you may need to change then environment vars in the task |
| http_store_ephemeral      | no       | false                                              | By default (false), the pod is managed as a systemd service. If set to true, the pod runs directly using Podman and requires manual management |

## Dependencies

- containers.podman

## Example Playbook

```
- name: Install and http_store service
  hosts: http_store
  roles:
    - setup_http_store
  vars:
    http_store_container_name: "iso store"
```
