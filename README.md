:rocket: Easily manage and configure firebase environmental variables without diving through the docs.

### 🥳 Setting environmental variables
To set new `environmental variables` for your project, use `firebase functions:config:set` command in the `Firebase CLI`. Keys
can be namespaced using periods. Only `lowercase` characters are accepted.

```bash
firebase functions:config:set someservice.key="THE API KEY" someservice.id="THE CLIENT ID"
```

### 🤖 Retrieve current config
To see the `environmental variables` currently set for your project, use `firebase functions:config:get`. The output in JSON format
```js
{
  "someservice": {
    "key":"THE API KEY",
    "id":"THE CLIENT ID"
  }
}
```

#### 🏠 Accessing environmental variables at runtime
You can use `functions.config()` to retrieve an environmental variable

```js
const functions = require('firebase-functions');
const request = require('request-promise');

exports.userCreated = functions.firestore.document("/user/{id}").onCreate((snap, context) => {
    return request({ 
        url: "https://someserver.com/api/xxx/",
        headers: {
            Authorization: "Bearer ${functions.config().someservice.key}"
        }
    });
});
```