<div align="center">
<img src="https://github.com/NGcodeX/NGcodeX_Server/blob/main/.github/workflows/private/NGcodeX%20server.png?raw=true">
</div>

# NGcodeX_Server
✔NGcodeX also has a hosting side that allows you to deploy your projects. Be the first to contribute to and benefit from a free deployment. THANKS

<h1><a href="https://github.com/NGcodeX/NGcodeX_WebSite">NGcodeX site under development</a></h1>

# ph-node-api

[![CircleCI](https://dl.circleci.com/status-badge/img/gh/PlanetHoster/ph-node-api/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/PlanetHoster/ph-node-api/tree/main)

[![NPM](https://nodei.co/npm/ph-node-api.png)](https://nodei.co/npm/ph-node-api/)

NodeJS PlanetHoster API integration.

Please refer to the documentation of the [NGcodeX-PlanetHoster API](https://apidoc.planethoster.com/) for all endpoints details.

## Installation
```
npm install ph-node-api
```

## Usage
```javascript
const PhNodeApi = require('ph-node-api');

async function testConnection(api) {
  try {
    console.log(await api.testConnection());
  } catch (e) {
    console.log(e);
  }
}

const api = new PhNodeApi({
  api_key: 'API_KEY',
  api_user: 'API_USER'
});

testConnection(api);
```
