# AuthManager


The user registration state is recorded in the browser cookies with two keys (`user` and `token`).

The `user` and `token` keys are serialised and encoded using `urlEncode`.
The user key has the following signature
```js
type User = {
   id: string
}
```
The `token` key and has the following signature
```js
type Token = {
access_token: string,
token_type: "Bearer"
expires_in: Date,
refresh_token: string
}
```
## Example
Using ESM modules
```js
import AuthManager from 'auth-manager'
```
### Methods
**Check is user is logged in**
```js
const isLoggedIn = AuthManager.isLoggedIn();
```
**Login a user**

To log in a user with `userId` make a call to the `login` method like
```
AuthManager.login({id: userId}, [1 week from now] )
```
the second argument is the date up to when the login state of the user will be persisted in the browser cookie (given as JavaScript date)
