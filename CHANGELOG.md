# Change Log

All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/) and [Keep a changelog](https://github.com/olivierlacan/keep-a-changelog).

## [Unreleased](https://github.com/idealista/clickhouse_role/tree/develop)

## [3.3.3(https://github.com/idealista/clickhouse_role/tree/3.3.3 (2023-03-27)

### :repeat: Updated

- [#50](https://github.com/idealista/clickhouse_role/issues/50) [REFACTOR] Adecuate service file changes to default CH version

### :hammer_and_wrench: Fixed

- Some typos and quotation

## [3.3.2](https://github.com/idealista/clickhouse_role/tree/3.3.2 (2023-01-18)

### :heavy_plus_sign: Added

- [#44](https://github.com/idealista/clickhouse_role/issues/44) Allow extra packages installation.

### :hammer_and_wrench: Fixed

- [#45](https://github.com/idealista/clickhouse_role/issues/45) Ensure existence of base path where clickhouse will be installed

## [3.3.1](https://github.com/idealista/clickhouse_role/tree/3.3.1) (2023-01-18)

### :heavy_plus_sign: Added

- [#41](https://github.com/idealista/clickhouse_role/issues/41) add TTL to system tables and default TTL values.

## [3.3.0](https://github.com/idealista/clickhouse_role/tree/3.3.0) (2022-11-12)

### :hammer_and_wrench: Fixed

- [#36](https://github.com/idealista/clickhouse_role/issues/36) Ansible galaxy meta malformed

### :heavy_plus_sign: Added

- [#35](https://github.com/idealista/clickhouse_role/issues/35) Clickhouse copier basic configuration 

### :repeat: Updated

- [#34](https://github.com/idealista/clickhouse_role/issues/34) The Clickhouse JDBC engine requirements installation

## [3.2.1](https://github.com/idealista/clickhouse_role/tree/3.2.1) (2022-08-30)

### :hammer_and_wrench: Fixed

- [#30](https://github.com/idealista/clickhouse_role/issues/30) Fixed clickhouse server fails after upgrading

## [3.2.0](https://github.com/idealista/clickhouse_role/tree/3.2.0) (2022-06-01)

### :heavy_plus_sign: Added

- [#26](https://github.com/idealista/clickhouse_role/issues/26) New feature to manage GRANT perms and privs
- Corresponding vars to use that feature
- Testing vars for this feature in molecule/group_vars
- Necesary templates

### :hammer_and_wrench: Fixed

- Tasks with no_log set to False

### :repeat: Updated

- Readme
- Test requirements Ansible version to 5.2.0
- Task tags
- Clickhouse default version

## [3.1.1](https://github.com/idealista/clickhouse_role/tree/3.1.1) (2022-04-29)

### :hammer_and_wrench: Fixed

- [#23](https://github.com/idealista/clickhouse_role/issues/23) Fixed task trying to remove '_temporary_and_external_tables' database @santi-eidu

## [3.1.0](https://github.com/idealista/clickhouse_role/tree/3.1.0) (2022-02-14)

### :heavy_plus_sign: Added

- Option to use custom config xml files
- [#18](https://github.com/idealista/clickhouse_role/issues/18) Option to create and remove basic users, roles, profiles, quotas, etc @ultraheroe

### :repeat: Updated

- Default ClickHouse version.
- Requirements versions.
- Readme instructions.
- Molecule verify update to use checksum instead of the deprecated command.
- Default molecule scenario and tests
- Tasks orders and role files skeleton
- [#20](https://github.com/idealista/clickhouse_role/issues/20) clickhouse_macros var refactor @ultraheroe

### :hammer_and_wrench: Fixed

- [#16](https://github.com/idealista/clickhouse_role/issues/16) Fix missing user, password and compression values in remote_servers @ultraheroe
- [#14](https://github.com/idealista/clickhouse_role/issues/14) Wait for service listening @jmonterrubio

## [3.0.1](https://github.com/idealista/clickhouse_role/tree/3.0.1) (2021-12-14)

### :hammer_and_wrench: Fixed

- [#8](https://github.com/idealista/clickhouse_role/issues/8) Remove ansible deprecation warning @Pablohn26
- [#10](https://github.com/idealista/clickhouse_role/issues/10) Fix paths permissions @ultraheroe
- [#11](https://github.com/idealista/clickhouse_role/issues/10) Allow custom tag values for replicated macro var @ultraheroe

### :heavy_plus_sign: Added

- Add .gitattributes.
- Add option to set CH release branch version.

### :repeat: Changed

- Update CH default version
- Update .travis python version to 3.9
- Update test-requirements, ansible, molecule, etc
- Update Readme

## [3.0.0](https://github.com/idealista/clickhouse_role/tree/3.0.0) (2021-11-23)

### :hammer_and_wrench: Fixed

- [#5](https://github.com/idealista/clickhouse_role/issues/5) Defined hkp apt keyserver protocol

### :heavy_plus_sign: Added

- [#4](https://github.com/idealista/clickhouse_role/issues/4) Required vars for new config templates

### :repeat: Changed

- [#4](https://github.com/idealista/clickhouse_role/issues/4) Fully parametrized config files
- .gitignore rules for various IDEs
- Deleted old stretch distro and add bullseye to .travis.yml
- Update test-requirements versions
- Update default version to latest (at this moment v21.11.2.2)
- Check how to check installed version
- Update molecule config and vars

## [2.0.0](https://github.com/idealista/clickhouse_role/tree/2.0.0) (2020-11-18)

- *[#1](https://github.com/idealista/clickhouse_role/issues/1) Fix mismatched var names* @frantsao
- *Fix systemd service config: prevent restarting after unit file changes; fix reloading (needs /bin/kill)* @frantsao
- *Fix default database creation* @frantsao
- *Fix missing listening host templating in config.xml* @frantsao
- *Fix admin user templating* @frantsao

### Added

- *Added var in order to control service behaviour in config changes* @frantsao

### Changed

- *Renamed vars in order to differentiate from other roles vars (BREAKING)* @frantsao

## [1.0.0](https://github.com/idealista/clickhouse_role/tree/1.0.0) (2020-11-03)

### Added

- *First version* @xtianae7
