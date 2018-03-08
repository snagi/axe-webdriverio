# axe-webdriverio
Provides bindings for AXE with WebdriverIO

## Getting Started

Install [Node.js](https://docs.npmjs.com/getting-started/installing-node) if you haven't already. For running axe-webdriverio tests read more about https://github.com/webdriverio/webdriverio/blob/master/README.md

> For more information on setting up webdriverIO tests see http://webdriver.io/guide.html


Install axe-webdriverio and its dependencies: `npm install axe-webdriverio`

## Usage

It provides the bindings over webdriverjs libraries which uses a chainable API to assist in injecting, configuring and analyzing using aXe with Selenium WebDriverJS.  As such, it is required to pass an instance of webdirverIO to AXE to perform the accessibility tests.

Here is an example of a script that will hand over the webdriverIO instance to axe-core of AXE tool to this repository, perform analysis and then log results to the console.

```javascript
var axeBuilder = require('axe-webdriverio');

return new Promise(function(resolve, reject){
new axeBuilder(driver).withTags(['wcag2a', 'wcag2aa']).analyze(resolve);
}.then(function(results){
console.log("AXE Accessibility Test Results: ", results);
} 
```

### axeBuilder(driver)

Constructor for the AxeBuilder helper. You must pass an instance of webdriverIO as the first and only argument.

### axeBuilder#withTags(wcag_standards)

Limits analysis to only those with the specified rule IDs. Accepts a String of a single tag or an Array of multiple tags.

### axeBuilder#analyze(callback:Function)

Performs analysis and passes the result object to the provided callback function or promise function. Does not chain as the operation is asynchronous

axeBuilder(driver)
  .analyze(function (results) {
    console.log(results);
  });
Using the returned promise (optional):

axeBuilder(driver)
  .analyze()
  .then(function (results) {
    console.log(results);
  });

