# primo-explore-report-problem

![Build Status](https://api.travis-ci.org/alliance-pcsg/primo-explore-report-problem.svg)
[![npm](https://img.shields.io/npm/v/primo-explore-report-problem.svg)](https://www.npmjs.com/package/primo-explore-report-problem)

## Features
A banner with a link to report a problem/bug appears below the "send to" actions in the details view. The text of the banner is configurable, and clicking the button will redirect to an external URL and append the docid of the record the patron was viewing to that URL.

### Screenshot
![screenshot](screenshot.png)

## Install
1. Make sure you've installed and configured [primo-explore-devenv](https://github.com/ExLibrisGroup/primo-explore-devenv).
2. Navigate to your template/central package root directory. For example:
    ```
    cd primo-explore/custom/MY_VIEW_ID
    ```
3. If you do not already have a `package.json` file in this directory, create one:
    ```
    npm init -y
    ```
4. Install this package:
    ```
    npm install primo-explore-report-problem --save-dev
    ```

## Usage
Once this package is installed, add `reportProblem` as a dependency for your custom module definition.

```js
var app = angular.module('viewCustom', ['reportProblem'])
```

Note: If you're using the `--browserify` build option, you will need to first import the module with:

```javascript
import 'primo-explore-report-problem';
```

You can configure the banner by passing a configuration object. All properties are required.

| name      | type         | usage                                                                                   |
|-----------|--------------|-----------------------------------------------------------------------------------------|
| `message` | string       | banner text displayed next to the button.                                               |
| `button`  | string       | text displayed on the button itself.                                                    |
| `base`    | string (url) | base URL for your 'report a problem' page, to which the record's docid will be appended |

The code below adds a banner similar to the above image.

```js
app.constant('reportProblemOptions', {
  message: "See something that doesn't look right?",
  button: "Report a Problem",
  base: "http://my.library.edu/reportproblem/?permalink_path="
})
```

## Running tests
1. Clone the repo
2. Run `npm install`
3. Run `npm test`
