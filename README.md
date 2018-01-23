## GridRouter in docker
[![Build Status](https://travis-ci.org/iqoption/gridrouter-docker.svg?branch=add-travis)](https://travis-ci.org/iqoption/gridrouter-docker)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Set up [GridRouter](https://github.com/aerokube/ggr) in docker

#### Requirements

* `python`
* `docker`

#### Variables

```yaml
grid_router_version: 1.4.0 # Install GridRouter version
grid_router_path: /etc/grid-router # Path to GridRouter
grid_router_qouta_path: /etc/grid-router/quota # Path to GridRouter quota
grid_router_qouta_user: selenoid # GridRouter quota user
grid_router_qouta_password: selenoid # GridRouter quota password
grid_router_time_zone: Europe/Moscow # Timezone in container
grid_router_port: 4444 # GridRouter port
grid_router_sctl_version: 1.2.0 # sctl version — https://github.com/seleniumkit/sctl/releases
grid_router_docker_api_version: 1.24 # Docker api version (for GridRouter)
grid_router_host_list: group # Host list for selenoid.xml

grid_router_regions: # Hosts list per region
    - name: "region-1"
      hosts:
        - name: localhost
          port: 4444
          browser_count: 4


grid_router_browsers: # Browser list usage selenoid
  - name: "firefox"
    defaultVersion: "54.0"
    versions:
      - "54.0"
      - "53.0"
      - "52.0"
  - name: "chrome"
    defaultVersion: "59.0"
    versions:
      - "59.0"
      - "58.0"
      - "57.0"
  - name: "opera"
    defaultVersion: "45.0"
    versions:
      - "45.0"
      - "44.0"
      - "43.0"
```

You can override collection browsers `grid_router_browsers` according to your needs.
For example:
```yaml
grid_router_browsers:
    - name: "firefox"
      defaultVersion: "54.0"
      versions:
        - "54.0"
    - name: "chrome"
      defaultVersion: "59.0"
      versions:
        - "59.0"
    - name: "opera"
      defaultVersion: "45.0"
      versions:
        - "45.0"
```

All supported browsers see [here](https://github.com/aerokube/selenoid#ready-to-use-browser-images).

Ggr is [using](http://aerokube.com/ggr/latest/#_creating_users_file) htpasswd files to store authentication data. Passwords are stored in encrypted form.

#### Example

```yaml
---
- hosts: all
  vars:
    grid_router_path: "{{ ansible_env.HOME }}/grid-router"
    grid_router_qouta_path: "{{ ansible_env.HOME }}/grid-router/quota"
    grid_router_port: 4445
    
    grid_router_regions:
        - name: "region-1"
          hosts:
          - name: 192.168.1.1
            port: 4444
            browser_count: 4
          - name: 192.168.1.2
            port: 4445
            browser_count: 4            
            
    grid_router_browsers:
        - name: "chrome"
          defaultVersion: "62.0"
          versions:
            - "62.0"
            - "63.0"
  roles:
    - gridrouter-docker
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
