# think-mock

Mock data for ThinkJS3.

## Precondition

think-mock need Babel support! For:
  - @babel/plugin-proposal-class-properties
  - @babel/plugin-proposal-decorators
  
is used!Replace them with corresponding plugin if babel6 is used in your project!

1. Open Babel transform (Both development or production enviroment)
2. Add plugin to babel config

## How to Use

1. Config mock path, or use default
```js
  // config.js
  mock: path.join(think.ROOT_PATH, 'mock'), // default
```

2. Create mock file

```js
  // think.ROOT_PATH/mock/user/index.js
  module.exports = {
    mock: 'This is mock data.'
  }
```

3. Add mock to action or method

```js
// controller/user.js
const { mock } = think.Controller.prototype;
module.exports = class extends think.Controller {
  @mock
  indexAction() {
    // mockFile think.ROOT_PATH/mock/user/index.js
    return this.json({ data: 'This is real data.' });
  }

  @mock getUserInfo() {
    // mockFile think.ROOT_PATH/mock/user/getUserInfo.js
  }
}

// service/sms.js
const { mock } = think.Service.prototype;
module.exports = class extends think.Service {
  @mock
  sendMessage() {
    // mockFile think.ROOT_PATH/mock/service/sms/sendMessage.js
    return { data: 'This is real data.' };
  }
};

```
