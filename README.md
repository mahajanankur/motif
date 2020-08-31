# Motifer

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Motifer is a generic logs pattern manager build on top of Winston. It covers multiple usecases as follows.

  - Log pattern validation.
  - Consistent log pattern across the application.
  - ELK and Cloudtrail support.

### Overview

Motifer uses a number of open source projects to work properly:

* [Winston](https://github.com/winstonjs/winston)

And of course Motifer itself is open source with a public [repository](https://github.com/mahajanankur/motifer)
 on GitHub.

### Installation

Motider requires [Node.js](https://nodejs.org/) v4+ to run.

Install the dependencies and devDependencies and start the server.

```sh
$ npm i motifer
```

## Usage
The recommended way to use `motifer` is to create a logger. The
simplest way to do this is using `LoggerBuilder`:
Initialize the LoggerFactory object once and use it in different js files.
``` js
const { LoggerFactory } = require('motifer');

exports.logger = new LoggerFactory("app_name", "logfile.log", "log_level");
```
``` js
const { logger } = require('./index');
logger.setFilename(__filename);

const printLogs = args => {
        logger
            .setLevel("info")
            .setMessage(`The message to print ${args.subargs}`)
            .setArguments(args)
            .build();
    });
}
```

### LoggerFactory

The **object** has three parameter.

| Param | Description |Mandatory
| ------ | ------ | ------ |
| service | Application or service name. | Yes |
| path | Path of logfile with filename. | Yes |
| level | Default log level for the application. | Yes |


License
----

**Apache 2.0**


**Free Software, Hell Yeah!**
