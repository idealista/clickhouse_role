# Change Log

All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/) and [Keep a changelog](https://github.com/olivierlacan/keep-a-changelog).

## [Unreleased](https://github.com/idealista/clickhouse_role/tree/develop)

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
