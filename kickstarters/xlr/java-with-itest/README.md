# XL Release PLUGINNAME Plugin

[![Build Status][xlr-PLUGINNAME-plugin-travis-image]][xlr-PLUGINNAME-plugin-travis-url]
[![Codacy Badge][xlr-PLUGINNAME-plugin-codacy-image] ][xlr-PLUGINNAME-plugin-codacy-url]
[![Code Climate][xlr-PLUGINNAME-plugin-code-climate-image] ][xlr-PLUGINNAME-plugin-code-climate-url]
[![License: MIT][xlr-PLUGINNAME-plugin-license-image]][xlr-PLUGINNAME-plugin-license-url]
[![Github All Releases][xlr-PLUGINNAME-plugin-downloads-image]]()

## Preface

This document describes the functionality provided by the XL Release xlr-PLUGINNAME-plugin.

See the [XL Release reference manual](https://docs.xebialabs.com/xl-release) for background information on XL Release and release automation concepts.  

## Overview

The plugin provides the ability to ...

## Requirements

* **Requirements**
*  **XL Release**   8.5.0+

## Installation

*   Copy the latest JAR file from the [releases page](https://github.com/xebialabs-community/xlr-PLUGINNAME-plugin/releases) into the `XL_RELEASE_SERVER/plugins/__local__` directory.
*   Restart the XL Release server.

## Usage

\<Include usage instructions with screen shots.  Screen shots should go in the ./images directory\>

## Developers

### Prerequisites

1. You will need to have Docker and Docker Compose installed.
2. The XL-Release docker container expects to find a valid XL-Release license on your machine, at this location: ~/xl-licenses/xl-release-license.lic

### Build and package the plugin

Execute the following from the project root directory...

```bash
./gradlew clean assemble
```

Output will be placed in ./build/libs folder.

### To run integration tests

Execute the following from the project root directory...

```bash
./gradlew clean itest
```

The itest will set up a containerized xlr/\<???\> testbed using docker compose.

### To run demo or dev version

```bash
cd ./src/test/resources
docker-compose -f docker/docker-compose.yml up
```

NOTE:

1. XL Release will run on the [localhost port 15516](http://localhost:15516/)
2. The XL Release username / password is admin / admin

[xlr-PLUGINNAME-plugin-travis-image]: https://travis-ci.org/xebialabs-community/xlr-PLUGINNAME-plugin.svg?branch=master
[xlr-PLUGINNAME-plugin-travis-url]: https://travis-ci.org/xebialabs-community/xlr-PLUGINNAME-plugin

[xlr-PLUGINNAME-plugin-codacy-image]: https://api.codacy.com/project/badge/Grade/88dec34743b84dac8f9aaaa665a99207
[xlr-PLUGINNAME-plugin-codacy-url]: https://www.codacy.com/app/ladamato/xlr-PLUGINNAME-plugin

[xlr-PLUGINNAME-plugin-code-climate-image]: https://codeclimate.com/github/xebialabs-community/xlr-PLUGINNAME-plugin/badges/gpa.svg
[xlr-PLUGINNAME-plugin-code-climate-url]: https://codeclimate.com/github/xebialabs-community/xlr-PLUGINNAME-plugin

[xlr-PLUGINNAME-plugin-license-image]: https://img.shields.io/badge/License-MIT-yellow.svg
[xlr-PLUGINNAME-plugin-license-url]: https://opensource.org/licenses/MIT
[xlr-PLUGINNAME-plugin-downloads-image]: https://img.shields.io/github/downloads/xebialabs-community/xlr-PLUGINNAME-plugin/total.svg
