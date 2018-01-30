> DevOps Middleware based on Aliyun Container Service / Docker Service

## Feature

**Registry**

- Public Registry
	- aliyun docker registry
	- docker hub
- Private Registry
	- Aliyun Docker Registry
	- WMware Harbor 
	- Docker Registry


**Deploy to Docker Service**

- aliyun container service
- rancher (WIP)
- docker swarm (WIP)
- kubernetes (WIP)

## Architecture

![](./assets/comp-relation.png)

## Usage

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

<!-- coming soon -->

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

## Screenshot

![](./assets/screenshot-images.png)
![](./assets/screenshot-clusters.png)
![](./assets/screenshot-services.png)
![](./assets/screenshot-deploys-list.png)
![](./assets/screenshot-deploys-detail.png)

## Reference

- https://github.com/thonatos/opts-react
- https://github.com/thonatos/opts-egg
