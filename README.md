# Maidops  &middot;  [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/thonatos/maidops/blob/master/LICENSE)

Maidops is a  DevOps middleware based on Aliyun Container Service / Docker Service .

![](./assets/comp-relation.png)

## Features

### Manage Docker Images

- Public Registry
	- aliyun docker registry
	- docker hub
- Private Registry
	- Aliyun Docker Registry
	- WMware Harbor 
	- Docker Registry

### Deploy to Docker Service

- aliyun container service
- rancher (WIP)
- docker swarm (WIP)
- kubernetes (WIP)

## Installation

### Install from git

**opts-egg**

```
# download source
git clone https://github.com/thonatos/opts-egg.git
cd opts-egg
npm i

# config
touch app/config/config.prop.js

# run
npm run start
```

**opts-react**

```
# download source
git clone https://github.com/thonatos/opts-react
cd opts-react
npm i

# config
cd src/constants
vi index.js

```

### Install from docker-compose

**Docker Compose**

```
version: '2'
services:
  devops:
    image: implementsio/opts-egg:latest
    environment:
      - EGG_SERVER_ENV=prod  
    ports:
      - 7001
    volumes:
      - oss_volume:/nouse
      - ./opts-egg/config/config.prod.js:/usr/src/app/config/config.prod.js:ro
```

**Aliyun Container Service**

```
version: '2'
services:
  devops:
    image: implementsio/opts-egg:latest
    environment:
      - EGG_SERVER_ENV=prod  
    ports:
      - 7001
    volumes:
      - oss_volume:/nouse
      - /mnt/acs_mnt/ossfs/{YOUR_OSS_VOLUME_NAME}/opts-egg/config/config.prod.js:/usr/src/app/config/config.prod.js:ro
    labels:
      aliyun.scale: '1'
      aliyun.rolling_updates: 'true'
      aliyun.routing.port_7001: http://{YOUR_DOMAIN_NAME}
```

### Custom Config

**opts-egg**

```js
// {app_root}/app/config/config.prod.js

// replace with yours
exports.mongoose = {
  url: 'mongodb://localhost/devops',
  options: {},
};

exports.jwt = {
  secret: 'opts',
  enable: true,
  match: '/api',
};

// replace with yours
exports.administrator = {
  username: 'suyi',
  password: '123456',
  userrole: 'admin',
};

exports.notifications = {
  dingtalk: {
    type: 'dingtalk',
    callbackUrl: '',
  },
};
```

**opts-react**

```js
// replace with yours
exports.api_server = 'http://localhost:7001'
```

## Development

- https://github.com/thonatos/opts-react
- https://github.com/thonatos/opts-egg

***You can find the screenshots [here](./opts-react.md).***

## Contributing

###Suggestions

Please open an issue [here](https://github.com/thonatos/maidops/issues).

### License

Maidops is [MIT licensed](./LICENSE).