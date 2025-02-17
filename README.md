# github-node-pre-gyp
##### A node-pre-gyp module which provides the ability to publish to GitHub releases.

[![Coverage Status](https://coveralls.io/repos/github/bchr02/node-pre-gyp-github/badge.svg?branch=master)](https://coveralls.io/github/lurenzsgp/node-pre-gyp-github?branch=master)

## Usage
Instead of ```node-pre-gyp publish``` use **```github-node-pre-gyp publish```**

## Options for publish command
* --silent : Turns verbose messages off.
* --release : Publish the GitHub Release immediately instead of creating a Draft.

  For Ex. ```github-node-pre-gyp publish --release```

## Install
```javascript
npm install -g github-node-pre-gyp
```

## Configuration
This module is intended to be used with node-pre-gyp. Therefore, be sure to configure and install node-pre-gyp first. After having done that, within **```package.json```** update the ```binary``` properties ```host``` and ```remote_path``` so it matches the following format:

```
  "host": "https://github.com/[owner]/[repo]/releases/download/",
  "remote_path": "{version}"
```

Be sure to replace ```[owner]```, ```[repo]```, with actual values,
but DO NOT replace ```{version}``` with actual version.

***WARNING: Variable substitutions are not supported on the ```host``` property and on the ```remote_path``` only ```{version}``` placeholder is supported. The value of ```remote_path``` after substitution will become a release tag name. Do not use [forbidden git tag characters](https://git-scm.com/docs/git-check-ref-format) for ```version``` and ```remote_path``` properties.***

Within GitHub, create a new authorization:

1. go to Settings
2. click Personal access tokens
3. click Generate new token
4. Select "public_repo" and "repo_deployment"
5. Generate Token
6. copy the key that's generated and set NODE_PRE_GYP_GITHUB_TOKEN environment variable to it. Within your command prompt:

```
SET NODE_PRE_GYP_GITHUB_TOKEN=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

## Example (Publish to GitHub as a Draft Release)
1. node-pre-gyp configure
2. node-pre-gyp build
3. node-pre-gyp package
4. github-node-pre-gyp publish

## Example (Publish to GitHub as a Release)
1. node-pre-gyp configure
2. node-pre-gyp build
3. node-pre-gyp package
4. github-node-pre-gyp publish --release
