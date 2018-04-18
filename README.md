## GridRouter in docker
[![Build Status](https://travis-ci.org/iqoption/gridrouter-docker.svg?branch=add-travis)](https://travis-ci.org/iqoption/gridrouter-docker)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Set up [GridRouter](https://github.com/aerokube/ggr) in docker

#### Requirements

* `python`
* `docker`

#### Variables

```yaml
grid_router_version: 1.5.3 # Install GridRouter version
grid_router_path: /etc/grid-router # Path to GridRouter
grid_router_qouta_path: /etc/grid-router/quota # Path to GridRouter quota
grid_router_qouta_user: selenoid # GridRouter quota user
grid_router_time_zone: Europe/Moscow # Timezone in container
grid_router_port: 4444 # GridRouter port
grid_router_sctl_version: 1.2.0 # sctl version — https://github.com/seleniumkit/sctl/releases
grid_router_host_list: group # Host list for selenoid.xml

grid_router_regions: # Hosts list per region
  - name: "region-1"
    hosts:
      - name: localhost[01:10].site.com # You can usage pattern [01:N]
        port: 4444
        browser_count: 5

grid_router_browsers: # Browser list usage selenoid
  - name: "firefox"
    defaultVersion: "59.0"
    versions:
      - "59.0"
      - "58.0"
      - "57.0"
      - "56.0"
      - "55.0"
  - name: "chrome"
    defaultVersion: "65.0"
    versions:
      - "65.0"
      - "64.0"
      - "63.0"
      - "62.0"
      - "61.0"
  - name: "opera"
    defaultVersion: "52.0"
    versions:
      - "52.0"
      - "51.0"
      - "50.0"
```

You can override collection browsers `grid_router_browsers` according to your needs.
For example:
```yaml
grid_router_browsers:
  - name: "firefox"
    defaultVersion: "59.0"
    versions:
      - "59.0"
  - name: "chrome"
    defaultVersion: "65.0"
    versions:
      - "65.0"
  - name: "opera"
    defaultVersion: "52.0"
    versions:
      - "52.0"
```

All supported browsers see [here](https://github.com/aerokube/selenoid#ready-to-use-browser-images).

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
        - name: 192.168.1.[1:2]
          port: 4444
          browser_count: 4

    grid_router_browsers:
      - name: "chrome"
        defaultVersion: "65.0"
        versions:
          - "65.0"
          - "64.0"
          - "63.0"
          - "62.0"
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
