## GridRouter in docker

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
* `grid_router_docker_api_version`: [Default: `1.24`] Docker api version (for GridRouter)
* `grid_router_host_list`: [Default: `group1`]
* `grid_router_region`: [Default: `region1`]
* `grid_router_host_name`: [Default: `selenoid[1:10].example.com`] Hostname selenoid

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
