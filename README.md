# on-syslog [![Build Status](https://travis-ci.org/RackHD/on-syslog.svg?branch=master)](https://travis-ci.org/RackHD/on-syslog) [![Code Climate](https://codeclimate.com/github/RackHD/on-syslog/badges/gpa.svg)](https://codeclimate.com/github/RackHD/on-syslog) [![Coverage Status](https://coveralls.io/repos/RackHD/on-syslog/badge.svg?branch=master&service=github)](https://coveralls.io/github/RackHD/on-syslog?branch=master)

test commit #1

`on-syslog` provides a syslog service that routes syslog messages into the
RackHD workflow engine

Copyright 2015, EMC, Inc.

## installation

    rm -rf node_modules
    npm install
    npm run apidoc

## running

Note: requires MongoDB and RabbitMQ to be running to start correctly.

    sudo node index.js

## CI/testing

To run tests from a developer console:

    npm test

To run tests and get coverage for CI:

    # verify hint/style
    ./node_modules/.bin/jshint -c .jshintrc --reporter=checkstyle lib index.js > checkstyle-result.xml || true
    ./node_modules/.bin/istanbul cover -x "**/spec/**" _mocha -- $(find spec -name '*-spec.js') -R xunit-file --require spec/helper.js
    ./node_modules/.bin/istanbul report cobertura
    # if you want HTML reports locally
    ./node_modules/.bin/istanbul report html


## Building

Unversioned packages are built automatically from travis-ci and uploaded to bintray.com. Using
this repository is detailed in [the docs](http://rackhd.readthedocs.org/en/latest/rackhd/ubuntu_package_installation.html).

Build scripts are placed in the `extra/` directory.

  * `.travis.yml` will call the appropriate scripts in `extra/` to build an unversioned package.
  * `extra/make-sysdeps.sh` can be used to install system level packages in a Ubuntu system.
  * `extra/make-cicd.sh` will perform all the necessary build steps to generate a version package.

If you want to build your own versioned packages, you can use the Vagrantfile provided in `extra/`.  Simply perform `vagrant up` and it will run all the necessary steps.

