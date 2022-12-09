# Terraform

## Output of commands

1. `terraform show`

```bash
# docker_container.nginx:
resource "docker_container" "nginx" {
  attach            = false
  command           = [
      "nginx",
      "-g",
      "daemon off;",
  ]
  cpu_shares        = 0
  entrypoint        = [
      "/docker-entrypoint.sh",
  ]
  env               = []
  gateway           = "172.17.0.1"
  hostname          = "631e7f5f9224"
  id                = "631e7f5f92243766c12c924331ee41666cfe0af540c50614bbdf6d33aa7267ac"
  image             = "sha256:835769b1adc00213f0a8fc55ba2ba56f2fb2eb8684b54b0afa3400000f1a73a8"
  init              = false
  ip_address        = "172.17.0.2"
  ip_prefix_length  = 16
  ipc_mode          = "private"
  log_driver        = "json-file"
  logs              = false
  max_retry_count   = 0
  memory            = 0
  memory_swap       = 0
  must_run          = true
  name              = "tutorial"
  network_data      = [
      {
          gateway                   = "172.17.0.1"
          global_ipv6_address       = ""
          global_ipv6_prefix_length = 0
          ip_address                = "172.17.0.2"
          ip_prefix_length          = 16
          ipv6_gateway              = ""
          network_name              = "bridge"
      },
  ]
  network_mode      = "default"
  privileged        = false
  publish_all_ports = false
  read_only         = false
  remove_volumes    = true
  restart           = "no"
  rm                = false
  security_opts     = []
  shm_size          = 64
  start             = true
  stdin_open        = false
  tty               = false

  ports {
      external = 8000
      internal = 80
      ip       = "0.0.0.0"
      protocol = "tcp"
  }
}

# docker_image.nginx:
resource "docker_image" "nginx" {
  id           = "sha256:835769b1adc00213f0a8fc55ba2ba56f2fb2eb8684b54b0afa3400000f1a73a8nginx:latest"
  keep_locally = false
  latest       = "sha256:835769b1adc00213f0a8fc55ba2ba56f2fb2eb8684b54b0afa3400000f1a73a8"
  name         = "nginx:latest"
  repo_digest  = "nginx@sha256:ab589a3c466e347b1c0573be23356676df90cd7ce2dbf6ec332a5f0a8b5e59db"
}
```

2. `terraform state list`

```bash
docker_container.nginx
docker_image.nginx
```

3. `terraform apply`

```bash
docker_image.nginx: Refreshing state... [id=sha256:835769b1adc00213f0a8fc55ba2ba56f2fb2eb8684b54b0afa3400000f1a73a8nginx:latest]
docker_container.nginx: Refreshing state... [id=631e7f5f92243766c12c924331ee41666cfe0af540c50614bbdf6d33aa7267ac]

Terraform used the selected providers to generate the following
execution plan. Resource actions are indicated with the following
symbols:
-/+ destroy and then create replacement

Terraform will perform the following actions:

# docker_container.nginx must be replaced
-/+ resource "docker_container" "nginx" {
    + bridge            = (known after apply)
    ~ command           = [
        - "nginx",
        - "-g",
        - "daemon off;",
      ] -> (known after apply)
    + container_logs    = (known after apply)
    - cpu_shares        = 0 -> null
    - dns               = [] -> null
    - dns_opts          = [] -> null
    - dns_search        = [] -> null
    ~ entrypoint        = [
        - "/docker-entrypoint.sh",
      ] -> (known after apply)
    ~ env               = [] -> (known after apply)
    + exit_code         = (known after apply)
    ~ gateway           = "172.17.0.1" -> (known after apply)
    - group_add         = [] -> null
    ~ hostname          = "631e7f5f9224" -> (known after apply)
    ~ id                = "631e7f5f92243766c12c924331ee41666cfe0af540c50614bbdf6d33aa7267ac" -> (known after apply)
    ~ init              = false -> (known after apply)
    ~ ip_address        = "172.17.0.2" -> (known after apply)
    ~ ip_prefix_length  = 16 -> (known after apply)
    ~ ipc_mode          = "private" -> (known after apply)
    - links             = [] -> null
    - log_opts          = {} -> null
    - max_retry_count   = 0 -> null
    - memory            = 0 -> null
    - memory_swap       = 0 -> null
      name              = "tutorial"
    ~ network_data      = [
        - {
            - gateway                   = "172.17.0.1"
            - global_ipv6_address       = ""
            - global_ipv6_prefix_length = 0
            - ip_address                = "172.17.0.2"
            - ip_prefix_length          = 16
            - ipv6_gateway              = ""
            - network_name              = "bridge"
          },
      ] -> (known after apply)
    - network_mode      = "default" -> null
    - privileged        = false -> null
    - publish_all_ports = false -> null
    ~ security_opts     = [] -> (known after apply)
    ~ shm_size          = 64 -> (known after apply)
    - sysctls           = {} -> null
    - tmpfs             = {} -> null
      # (12 unchanged attributes hidden)

    + healthcheck {
        + interval     = (known after apply)
        + retries      = (known after apply)
        + start_period = (known after apply)
        + test         = (known after apply)
        + timeout      = (known after apply)
      }

    + labels {
        + label = (known after apply)
        + value = (known after apply)
      }

    ~ ports {
        ~ external = 8000 -> 8080 # forces replacement
          # (3 unchanged attributes hidden)
      }
  }

Plan: 1 to add, 0 to change, 1 to destroy.
╷
│ Warning: Deprecated attribute
│
│   on main.tf line 18, in resource "docker_container" "nginx":
│   18:   image = docker_image.nginx.latest
│
│ The attribute "latest" is deprecated. Refer to the provider
│ documentation for details.
│
│ (and one more similar warning elsewhere)
╵

Do you want to perform these actions?
Terraform will perform the actions described above.
Only 'yes' will be accepted to approve.

Enter a value: yes

docker_container.nginx: Destroying... [id=631e7f5f92243766c12c924331ee41666cfe0af540c50614bbdf6d33aa7267ac]
docker_container.nginx: Destruction complete after 0s
docker_container.nginx: Creating...
docker_container.nginx: Creation complete after 1s [id=389885d0879a194d82516d912be5591de39f6539e50e78d086360036851a6eca]
╷
│ Warning: Deprecated attribute
│
│   on main.tf line 18, in resource "docker_container" "nginx":
│   18:   image = docker_image.nginx.latest
│
│ The attribute "latest" is deprecated. Refer to the provider
│ documentation for details.
│
│ (and one more similar warning elsewhere)
╵

Apply complete! Resources: 1 added, 0 changed, 1 destroyed.
```

4. `terraform output`

```bash
container_id = "e5cf690cdbab43438926558001bc4b8dde50a90e5fc5e4200b9a8754200ffadc"
image_id = "sha256:835769b1adc00213f0a8fc55ba2ba56f2fb2eb8684b54b0afa3400000f1a73a8nginx:latest"
```
