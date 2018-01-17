## GridRouter in docker
[![Build Status](https://travis-ci.org/iqoption/gridrouter-docker.svg?branch=add-travis)](https://travis-ci.org/iqoption/gridrouter-docker)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Set up [GridRouter](https://github.com/aerokube/ggr) in docker

#### Requirements

* `python`
* `docker`

#### Variables

* `grid_router_version`: [Default: `1.4.0`] Install GridRouter version
* `grid_router_qouta_path`: [Default: `/etc/grid-router/quota`] Path to GridRouter quota
* `grid_router_qouta_password`: [Default: `selenoid`] GridRouter quota password
* `grid_router_qouta_user`: [Default: `selenoid`] GridRouter quota user
* `grid_router_gr_path`: [Default: `/etc/grid-router`] Path to GridRouter
* `grid_router_port`: [Default: `4444`] GridRouter port
* `grid_router_docker_api_version`: [Default: `1.24`] Docker api version (for GridRouter)
* `grid_router_host_list`: [Default: `group1`]
* `grid_router_region`: [Default: `region1`]
* `grid_router_host_name`: [Default: `selenoid[1:10].example.com`] Hostname selenoid
* `grid_router_time_zone`: [Default: `Europe/Moscow`] Timezone in container
* `grid_router_browsers`: This array include usage browsers

You can override collection browsers `grid_router_browsers` according to your needs.
For example:
```yaml
grid_router_browsers:
    - name: "firefox"
      defaultVersion: "54.0"
      versions:
        - "54.0"
        - "53.0"
    - name: "chrome"
      defaultVersion: "59.0"
      versions:
        - "59.0"
        - "58.0"
    - name: "opera"
      defaultVersion: "45.0"
      versions:
        - "45.0"
        - "44.0"
```

All supported browsers see [here](https://github.com/aerokube/selenoid#ready-to-use-browser-images).

Ggr is [using](http://aerokube.com/ggr/latest/#_creating_users_file) htpasswd files to store authentication data. Passwords are stored in encrypted form.

#### Example

```yaml
---
- hosts: all
  roles:
  - gridrouter
```

## Dependencies

None

## Contributing
1. Fork it;
2. Create your feature branch: `git checkout -b my-new-feature`;
3. Commit your changes: `git commit -am 'Add some feature'`;
4. Push to the branch: `git push origin my-new-feature`;
5. Submit a pull request.

## License
See LICENSE.md
