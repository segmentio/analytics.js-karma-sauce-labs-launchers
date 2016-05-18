# analytics.js-karma-sauce-labs-launchers

A centralized list of Sauce Labs browsers used when testing Analytics.js components.

## Usage

An example `karma.conf.js`:

```js
'use strict';

var customLaunchers = require('@segment/analytics.js-karma-sauce-labs-launchers');

module.exports = function(config) {
  if (!process.env.SAUCE_USERNAME || !process.env.SAUCE_ACCESS_KEY) {
    throw new Error('SAUCE_USERNAME and SAUCE_ACCESS_KEY environment variables are required but are missing');
  }

  config.set({
    singleRun: true,

    browsers: ['PhantomJS'].concat(Object.keys(customLaunchers)),

    customLaunchers: customLaunchers,

    sauceLabs: {
      testName: require('./package.json').name
    }
  });
};
```
