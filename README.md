## GridRouter in docker

Set up [GridRouter](https://github.com/aerokube/ggr) in docker

#### Requirements

* `python`
* `docker`

#### Variables

* `grid_router_version`: [Default: `1.3.0`] Install GridRouter version
* `grid_router_qouta_path`: [Default: `/etc/grid-router/quota`] Path to GridRouter quota
* `grid_router_qouta_password`: [Default: `selenoid`] GridRouter quota password
* `grid_router_qouta_user`: [Default: `selenoid`] GridRouter quota user
* `grid_router_gr_path`: [Default: `/etc/grid-router`] Path to GridRouter
* `grid_router_docker_api_version`: [Default: `1.24`] Docker api version (for GridRouter)

Ggr is [using](http://aerokube.com/ggr/latest/#_creating_users_file) htpasswd files to store authentication data. Passwords are stored in encrypted form.

## Dependencies

None

#### Example

First step you need edit `./files/input.json`. This file help generate browser.xml

```
"group1": {
  "wz": {
    "selenoid[1:50].youhost.com": {
      "port": 4444,
      "count": 1
    }
  }
```

1. Change `group1` you name group host;
2. Change host (or use many hosts);
3. Change group in quota browser block (use name group from 1 step).

```yaml
---
- hosts: all
  roles:
  - gridrouter
```
