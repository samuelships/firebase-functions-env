:rocket: Easily manage and configure firebase environmental variables without diving through the docs.

### 🥳 Setting environmental variables
To set new `environmental variables` for your project, use `firebase functions:config:set` command in the `Firebase CLI`. Keys
can be namespaced using periods. Only `lowercase` characters are accepted.

```bash
firebase functions:config:set someservice.key="THE API KEY" someservice.id="THE CLIENT ID"
```

