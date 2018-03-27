# Maidops  &middot;  [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/thonatos/maidops/blob/master/LICENSE)

[![CircleCI](https://circleci.com/gh/thonatos/opts-egg.svg?style=svg)](https://circleci.com/gh/thonatos/opts-egg)

Maidops is a  DevOps Middleware based on Docker / Kuberntes .

![](./assets/comp-relation.png)

## Features

- image management
- webhook
	- Docker Hub
	- Harbor
	- Aliyun Container Registry
- notification
	- dingtalk
- docker / kubernets deployment
	- aliyun container service
	- kubernetes
	- rancher (WIP)

## Installation

### Install from git

**opts-egg**

```
# download source
git clone https://github.com/thonatos/opts-egg.git
cd opts-egg
npm i

# config or export envs
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
vi env.{env}

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
      - EGG_MAIDOPS_ACCESS_TOKEN=
      - EGG_WHITELIST=
      - EGG_MAIDOPS_ACCESS_TOKEN=
      - EGG_ADMINISTRATOR_USERNAEM=
      - EGG_ADMINISTRATOR_PASSWORD=
      - EGG_MONGOOSE_URL=
      - EGG_DINGTALK_ROBOT_URL=
    ports:
      - 7001
```

**Aliyun Container Service**

```
version: '2'
services:
  devops:
    image: implementsio/opts-egg:latest
    environment:
      - EGG_SERVER_ENV=prod  
      - EGG_SERVER_ENV=prod
      - EGG_MAIDOPS_ACCESS_TOKEN=
      - EGG_WHITELIST=
      - EGG_MAIDOPS_ACCESS_TOKEN=
      - EGG_ADMINISTRATOR_USERNAEM=
      - EGG_ADMINISTRATOR_PASSWORD=
      - EGG_MONGOOSE_URL=
      - EGG_DINGTALK_ROBOT_URL=      
    ports:
      - 7001
    # volumes:
    #  - oss_volume:/nouse
    #  - ./opts-egg/config/config.prod.js:/usr/src/app/config/config.prod.js:ro
    labels:
      aliyun.scale: '1'
      aliyun.rolling_updates: 'true'
      aliyun.routing.port_7001: http://{YOUR_DOMAIN_NAME}
```

## Development

- [opts-egg]
- [opts-react]

***You can find the screenshots [here](./opts-react.md).***

## Contributing

### Suggestions

Please open an issue [here](https://github.com/thonatos/maidops/issues).

### License

Maidops is [MIT licensed](./LICENSE).

[opts-react]: https://github.com/thonatos/opts-react
[opts-egg]: https://github.com/thonatos/opts-egg