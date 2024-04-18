# Clickhouse Ansible role

![GitHub release (latest by date)](https://img.shields.io/github/v/release/idealista/clickhouse_role?color=%23B62682)
[![Build Status](https://travis-ci.org/idealista/clickhouse_role.png)](https://travis-ci.org/idealista/clickhouse_role) [![Ansible Galaxy](https://img.shields.io/badge/galaxy-idealista.clickhouse_role-B62682.svg)](https://galaxy.ansible.com/idealista/clickhouse_role)

![Logo](https://raw.githubusercontent.com/idealista/clickhouse_role/main/logo.gif)

This ansible role installs [Clickhouse](https://clickhouse.com/) in a Debian environment. It has been tested for Debian bullseye.

This role has been generated using the [cookiecutter](https://github.com/cookiecutter/cookiecutter) tool, you can generate a similar role that fits your needs using the this [cookiecutter template](https://github.com/idealista/cookiecutter-ansible-role).

- [Getting Started](#getting-started-checkered_flag)
  - [Prerequisites](#prerequisites-ballot_box_with_check)
  - [Installing](#Installing-inbox_tray )
- [Usage](#usage-runner)
- [Testing](#testing-test_tube)
- [Built With](#built-with-building_construction)
- [Versioning](#versioning-card_file_box)
- [Authors](#authors-superhero)
- [License](#license-spiral_notepad)
- [Contributing](#contributing-construction_worker)

## Getting Started :checkered_flag:

These instructions will get you a copy of the role for your Ansible playbook. Once launched, it will install [Clickhouse](https://clickhouse.com/) in a Debian system.

### Prerequisites :ballot_box_with_check:

Ansible 5.x.x version installed.

Molecule 3.x.x version installed.

For testing purposes, [Molecule](https://molecule.readthedocs.io/) with [Docker](https://www.docker.com/) as driver and [Goss](https://github.com/aelsabbahy/goss) as verifier.

### Installing :inbox_tray:

Create or add to your roles dependency file (e.g requirements.yml):

```yml
- src: idealista.clickhouse_role
  scm: git
  version: 3.2.0
  name: clickhouse_role
```

Install the role with ansible-galaxy command:

```sh
ansible-galaxy install -p roles -r requirements.yml -f
```

Use in a playbook:

```yml
---
- hosts: someserver
  roles:
    - role: clickhouse_role
```

## Usage :runner:

Look to the [defaults](defaults/main.yml) properties file to see the possible configuration properties, it is very likely that you will not need to override any variables but don't forget to set your Admin user 🦸

- [`main.yml`](./defaults/main.yml) for superset general purpose vars.

### 👉 Don't forget

- 🦸 To set your Admin user and use a secure 🔑 password.
- 📝 To set the `clickhouse_custom_config_file_path` and / or `clickhouse_custom_users_file_path` if you are going to use custom config files.
  - 👉 See the [ClickHouse doc](https://clickhouse.com/docs/en/operations/configuration-files/).
- ☑️ To enable or disable using `clickhouse_role_manage_X` vars what things the role should manage.
- 📝 To set users, quotas, profiles, grants, databases to create.
  - ℹ️ Or to unset if you want to DROP things.
  - 👉 See the default molecule scenario [`group_vars`](./molecule/default/group_vars/clickhouse_group.yml) for more

### ❗ You must know

- ❗ To make us of the 'EXCEPT' clauses for [quota assignation](https://clickhouse.com/docs/en/sql-reference/statements/create/quota/) or [user grantees](https://clickhouse.com/docs/en/sql-reference/statements/create/user/#grantees) for example, you can add a minus or dash _( - )_ before the name.
- ❗ When setting `password_type` for users, it should be one of [this](https://clickhouse.com/docs/en/sql-reference/statements/create/user/#identification)
- ❗ When setting `keyed` for quota, it should be one of [this](https://clickhouse.com/docs/en/sql-reference/statements/create/quota/)
- ❗ In case you're using LDAP or Kerberos, set each with their own property `ldap_server` or 'kerberos' so `password_type` is not required
- ⚠️ `clickhouse_replicated_tables_macros` is deprecated, please use `clickhouse_macros` var

#### Users and roles

- ⚠️ Note that are two ways to set users for ClickHouse, `users.xml` or via SQL-query, to distinguish both methods note that in this role we use `clickhouse_custom_users_xml` and `clickhouse_custom_users` respectively (SQL recommended).
- ⚠️ When granting, you must know:
  - When performing the GRANT actions to maintain the perms & privs clean a "general" REVOKE is performed before GRANTing
  - There is an option to disable that before "GRANTS" clean up: `clickhouse_custom_grants_previous_cleanup`
  - When granting permissions and privileges the order of the items in definition list takes precedence, is recommended to do this grant from less to the most restrictive.
    - 👉 See example below, more at the default molecule scenario [`group_vars`](./molecule/default/group_vars/clickhouse_group.yml) for more.
  - Statements Aliases are valid, but not handled at "ansible level" so this results in task making comparisions like `privileges: [DELETE]` vs `system.grants access_type = ALTER DELETE` (from ClickHouse), so we recommend set "un-aliased" perms and privs.
  - When performing REVOKE or GRANT if a problem occurs may be result in unexpected / removed perms & privs in the ClickHouse DB ¡¡Be extra careful!!
  - You can GRANT a role to a role, or roles to users with `clickhouse_custom_grant_roles`.

##### Custom user definition example:

  ```yml
  clickhouse_custom_users:
    - user:
      name: "Takumi"
      password_type: plaintext_password
      password: "AE86"
      networks:
        - "IP '::/0'"
      settings:
        - "max_memory_usage = 10000000000"
      role:
        - projectd_members
        - tofu_shop
      profile:
        - default
      grantees:
        - projectd_members
      quota: "default"
      databases: [ProjectD]
      # ldap_server: project.d
      # kerberos: ""

  clickhouse_custom_grants:
  - on:
    databases: [Akina]
    tables: ["*"]
    privileges: [SELECT]
    to: [initial_d]
  - on:
    # cluster:
    databases: ["Akina"]
    tables: [calendar, records]
    # columns: [Notes]
    privileges: [ALL]
    to: [Takumi, Iketani]
    with_grant_option: True
  - on:
    # cluster:
    databases: ["Akina"]
    tables: [records]
    privileges: [SELECT, UPDATE]
    to: [Iketani]
    with_grant_option: False

  clickhouse_custom_grant_roles:
    - roles: [initial_d]
      to: [Takumi, Iketani]
      # cluster:
```

## Testing :test_tube:

### Install dependencies

```sh
pipenv install -r test-requirements.txt
```

For more information read the [pipenv docs](ipenv-fork.readthedocs.io/en/latest/).

### Testing

```sh
$ pipenv run molecule test
```

## Built With :building_construction:

![Ansible](https://img.shields.io/badge/ansible-4.10.0-green.svg)
![Molecule](https://img.shields.io/badge/molecule-3.5.2-green.svg)
![Docker](https://img.shields.io/badge/docker-5.0.3-blue.svg)
![Goss](https://img.shields.io/badge/goss-0.3.13-green.svg)

## Versioning :card_file_box:

For the versions available, see the [tags on this repository](https://github.com/idealista/clickhouse_role/tags).

Additionaly you can see what change in each version in the [CHANGELOG.md](CHANGELOG.md) file.

## Authors :superhero:

- **Idealista** - _Work with_ - [idealista](https://github.com/idealista)

See also the list of [contributors](https://github.com/idealista/clickhouse_role/contributors) who participated in this project.

## License :spiral_notepad:

![Apache 2.0 License](https://img.shields.io/hexpm/l/plug.svg)

This project is licensed under the [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license - see the [LICENSE](LICENSE) file for details.

## Contributing :construction_worker:

Please read [CONTRIBUTING.md](.github/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.
