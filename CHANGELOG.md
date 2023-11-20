# Changelog

All notable changes to this project will be documented in this file. See [standard-version](https://github.com/conventional-changelog/standard-version) for commit guidelines.

### [6.0.1](https://github.com/ipbrad/casbin-mongoose-adapter/compare/v6.0.0...v6.0.1) (2023-11-20)

## 6.0.0 (2023-11-20)


### ⚠ BREAKING CHANGES

* we will finally move to `ptype`, as discussed one year ago: https://github.com/pycasbin/sqlalchemy-adapter/issues/26#issuecomment-769799410 . It is also officially documented in the official site: https://casbin.org/docs/en/adapters#:~:text=Ptype%20Column.%20Name%20of%20this%20column%20should%20be%20ptype%20instead%20of%20p_type%20or%20Ptype

Co-authored-by: Shivansh Yadav <yadavshivansh@gmail.com>
* upgrade to Mongoose 6.x and drop Node 10 support
* This package has been rewritten to TypeScript.

Signed-off-by: Zxilly <zhouxinyu1001@gmail.com>
* Function name changed to separate it from mongo session transactions

* fix(adapter.js:savepolicy): empty model should not throw an MongoError, it should return false

Previously MongoError would have been thrown since it's trying to save an empty list.

* refactor(debug): add a warning when transaction starts or aborts instead of constant debugging

* test(unit/adapter.test.js): add unit tests for missing functions and add lcov reporter to nyc

* test(integration/adapter.test.js:savepolicy): add sinon to improve empty savePolicy testing

* test(integration/adapter.test.js): add more complex model and policy to test populated v0-v4 values

Previous models only populated fields 0-2

* test(integration/adapter.test.js): failing tests for non-synced adapter transactions

* feat(adapter.js): add support for addPolicies and removePolicies in replicaset environments

* feat(.travis.yml): initial replicaset configuration

- Try rs.initiate and then loop over rs.status to check whether replicaset has been configured

* test(helpers.js): change tests to replicaset for now

* test(.travis.yml): try Bottle-Mongo's Travis-CI setup

https://github.com/bottlepy/bottle-mongo/blob/master/.travis.yml

* test(helpers.js): change replicaset connections to 2 nodes

* test(.travis.yml): add rs.status() command to the end of before-script

* test(.travis.yml, rs_status.js): add more complicated replicaset status check

https://github.com/bottlepy/bottle-mongo/blob/f3a0187cc890ac8265840411e8cf77ed4020a0e4/.travis/rs_create.js

* docs(adapter.js): clarify savePolicyLine since it actually does not save anything

* improvement(adapter.js, errors.js): add functionality to automatically abort and commit transactions

* style(rs_status.js): remove double semicolon

* improvement(adapter.js, errors.js): allow synced adapter for all connections

MongoDB should handle error cases when trying to do transactions in improper environments. This
library should not govern it.

* style: raise errors from missing semicolons (eslint changes reverted)
* **package.json:** Async functions return promises which will inherenty break the expected return
values of all functions. (As an example from Boolean into Promise<Boolean>)

### Features

* add postinstall script ([af93ec8](https://github.com/ipbrad/casbin-mongoose-adapter/commit/af93ec8025f10bd761b47c276a841e368f61bc1a))
* add rewritten warning ([378197c](https://github.com/ipbrad/casbin-mongoose-adapter/commit/378197cf1afd82ba2ef1569c843f924ba5137b16))
* check if the word is already wrapped in quotes ([d31166e](https://github.com/ipbrad/casbin-mongoose-adapter/commit/d31166e3fd8f67eb6ffcff475a68916f61ce7f60))
* enable mongoose timestamps for casbin rule model via adapter options ([#71](https://github.com/ipbrad/casbin-mongoose-adapter/issues/71)) ([3dd8862](https://github.com/ipbrad/casbin-mongoose-adapter/commit/3dd8862f8eb452adc1365c96df55125561358bb1))
* implement UpdatableAdapter interface ([#49](https://github.com/ipbrad/casbin-mongoose-adapter/issues/49)) ([131a446](https://github.com/ipbrad/casbin-mongoose-adapter/commit/131a446b813b202d322ac0d0fc45d436e34832ca))
* update mongoose dependency to 7.3.4 ([#73](https://github.com/ipbrad/casbin-mongoose-adapter/issues/73)) ([bbc7953](https://github.com/ipbrad/casbin-mongoose-adapter/commit/bbc79536d6abf5aca92bd83e601a457104f0b02a))
* upgrade Mongoose ([#52](https://github.com/ipbrad/casbin-mongoose-adapter/issues/52)) ([fb53794](https://github.com/ipbrad/casbin-mongoose-adapter/commit/fb5379432397710a27570b116ea3f7459f4bd3b6))


### Bug Fixes

* **adapter:** expose mongoose instance as public property ([#54](https://github.com/ipbrad/casbin-mongoose-adapter/issues/54)) ([31e6ef9](https://github.com/ipbrad/casbin-mongoose-adapter/commit/31e6ef9f81aebba385d0b7a0e66960c23e316c4f))
* change p_type to ptype ([#61](https://github.com/ipbrad/casbin-mongoose-adapter/issues/61)) ([1167bed](https://github.com/ipbrad/casbin-mongoose-adapter/commit/1167bed29efc618f09fef7b7c98d8ff81520369f))
* filter model ([#19](https://github.com/ipbrad/casbin-mongoose-adapter/issues/19)) ([b583faf](https://github.com/ipbrad/casbin-mongoose-adapter/commit/b583faf63cb4bd0de9596d144cc1311acf3eeafd))
* fix broken links ([#74](https://github.com/ipbrad/casbin-mongoose-adapter/issues/74)) ([160f44c](https://github.com/ipbrad/casbin-mongoose-adapter/commit/160f44c79452ae939865ddc5de116983c9fcc340))
* fix different import action ([ddf23a7](https://github.com/ipbrad/casbin-mongoose-adapter/commit/ddf23a7a6fc1720b693285005da12e52fe5ab13c))
* fix multiple adapter ([#68](https://github.com/ipbrad/casbin-mongoose-adapter/issues/68)) ([49e69bc](https://github.com/ipbrad/casbin-mongoose-adapter/commit/49e69bc2f526fdb42b7410a04173c6b4c58bb635))
* fix wrong action with empty string ([#47](https://github.com/ipbrad/casbin-mongoose-adapter/issues/47)) ([f51fdde](https://github.com/ipbrad/casbin-mongoose-adapter/commit/f51fdde975df95a33c0b9bbcc8fdcf64b7af73a2))
* format issues ([d653519](https://github.com/ipbrad/casbin-mongoose-adapter/commit/d653519ec3cfc8b1f81d2a061dbb86df1a4df9c3))
* no longer support legacy require ([5b09912](https://github.com/ipbrad/casbin-mongoose-adapter/commit/5b09912a693a3cf6442d640fe4031938a373c820))
* token parsing issues if token contains delimeter ([cd695a6](https://github.com/ipbrad/casbin-mongoose-adapter/commit/cd695a68f7f45faaae065d4e37c7d4593f7d09b9))
* update lock file ([203cc98](https://github.com/ipbrad/casbin-mongoose-adapter/commit/203cc98d9db46e10319f89ea6ab3affe98c2098b))


### improvement

* **package.json:** upgrade Casbin to version 4.1.1 ([450efc3](https://github.com/ipbrad/casbin-mongoose-adapter/commit/450efc3f83fd93a18c49fe9c664671c4e23e21e4))


### WIP

* Synced Adapter ([#8](https://github.com/ipbrad/casbin-mongoose-adapter/issues/8)) ([6b46b3a](https://github.com/ipbrad/casbin-mongoose-adapter/commit/6b46b3a3f657b2762eb655b3c1b1b81a4a9534e7))

## [5.3.1](https://github.com/node-casbin/mongoose-adapter/compare/v5.3.0...v5.3.1) (2023-08-06)


### Bug Fixes

* fix broken links ([#74](https://github.com/node-casbin/mongoose-adapter/issues/74)) ([160f44c](https://github.com/node-casbin/mongoose-adapter/commit/160f44c79452ae939865ddc5de116983c9fcc340))

# [5.3.0](https://github.com/node-casbin/mongoose-adapter/compare/v5.2.0...v5.3.0) (2023-07-14)


### Features

* update mongoose dependency to 7.3.4 ([#73](https://github.com/node-casbin/mongoose-adapter/issues/73)) ([bbc7953](https://github.com/node-casbin/mongoose-adapter/commit/bbc79536d6abf5aca92bd83e601a457104f0b02a))

# [5.2.0](https://github.com/node-casbin/mongoose-adapter/compare/v5.1.1...v5.2.0) (2023-04-21)


### Features

* enable mongoose timestamps for casbin rule model via adapter options ([#71](https://github.com/node-casbin/mongoose-adapter/issues/71)) ([3dd8862](https://github.com/node-casbin/mongoose-adapter/commit/3dd8862f8eb452adc1365c96df55125561358bb1))

## [5.1.1](https://github.com/node-casbin/mongoose-adapter/compare/v5.1.0...v5.1.1) (2023-04-19)


### Bug Fixes

* fix multiple adapter ([#68](https://github.com/node-casbin/mongoose-adapter/issues/68)) ([49e69bc](https://github.com/node-casbin/mongoose-adapter/commit/49e69bc2f526fdb42b7410a04173c6b4c58bb635))

# [5.1.0](https://github.com/node-casbin/mongoose-adapter/compare/v5.0.0...v5.1.0) (2022-03-21)


### Bug Fixes

* format issues ([d653519](https://github.com/node-casbin/mongoose-adapter/commit/d653519ec3cfc8b1f81d2a061dbb86df1a4df9c3))
* token parsing issues if token contains delimeter ([cd695a6](https://github.com/node-casbin/mongoose-adapter/commit/cd695a68f7f45faaae065d4e37c7d4593f7d09b9))
* update lock file ([203cc98](https://github.com/node-casbin/mongoose-adapter/commit/203cc98d9db46e10319f89ea6ab3affe98c2098b))


### Features

* add postinstall script ([af93ec8](https://github.com/node-casbin/mongoose-adapter/commit/af93ec8025f10bd761b47c276a841e368f61bc1a))
* check if the word is already wrapped in quotes ([d31166e](https://github.com/node-casbin/mongoose-adapter/commit/d31166e3fd8f67eb6ffcff475a68916f61ce7f60))

# [5.0.0](https://github.com/node-casbin/mongoose-adapter/compare/v4.0.1...v5.0.0) (2022-03-13)


### Bug Fixes

* change p_type to ptype ([#61](https://github.com/node-casbin/mongoose-adapter/issues/61)) ([1167bed](https://github.com/node-casbin/mongoose-adapter/commit/1167bed29efc618f09fef7b7c98d8ff81520369f))


### BREAKING CHANGES

* we will finally move to `ptype`, as discussed one year ago: https://github.com/pycasbin/sqlalchemy-adapter/issues/26#issuecomment-769799410 . It is also officially documented in the official site: https://casbin.org/docs/adapters/

Co-authored-by: Shivansh Yadav <yadavshivansh@gmail.com>

## [4.0.1](https://github.com/node-casbin/mongoose-adapter/compare/v4.0.0...v4.0.1) (2022-01-31)


### Bug Fixes

* **adapter:** expose mongoose instance as public property ([#54](https://github.com/node-casbin/mongoose-adapter/issues/54)) ([31e6ef9](https://github.com/node-casbin/mongoose-adapter/commit/31e6ef9f81aebba385d0b7a0e66960c23e316c4f))

# [4.0.0](https://github.com/node-casbin/mongoose-adapter/compare/v3.1.1...v4.0.0) (2022-01-29)


### Features

* upgrade Mongoose ([#52](https://github.com/node-casbin/mongoose-adapter/issues/52)) ([fb53794](https://github.com/node-casbin/mongoose-adapter/commit/fb5379432397710a27570b116ea3f7459f4bd3b6))


### BREAKING CHANGES

* upgrade to Mongoose 6.x and drop Node 10 support

## [3.1.1](https://github.com/node-casbin/mongoose-adapter/compare/v3.1.0...v3.1.1) (2021-08-28)


### Bug Fixes

* fix wrong action with empty string ([#47](https://github.com/node-casbin/mongoose-adapter/issues/47)) ([f51fdde](https://github.com/node-casbin/mongoose-adapter/commit/f51fdde975df95a33c0b9bbcc8fdcf64b7af73a2))

# [3.1.0](https://github.com/node-casbin/mongoose-adapter/compare/v3.0.1...v3.1.0) (2021-08-03)


### Features

* implement UpdatableAdapter interface ([#49](https://github.com/node-casbin/mongoose-adapter/issues/49)) ([131a446](https://github.com/node-casbin/mongoose-adapter/commit/131a446b813b202d322ac0d0fc45d436e34832ca))

## [3.0.1](https://github.com/node-casbin/mongoose-adapter/compare/v3.0.0...v3.0.1) (2021-04-27)


### Bug Fixes

* no longer support legacy require ([5b09912](https://github.com/node-casbin/mongoose-adapter/commit/5b09912a693a3cf6442d640fe4031938a373c820))
