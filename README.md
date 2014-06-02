# sticky-identity

[![Build Status](https://travis-ci.org/bvalosek/sticky-identity.png?branch=master)](https://travis-ci.org/bvalosek/sticky-identity)
[![NPM version](https://badge.fury.io/js/sticky-identity.png)](http://badge.fury.io/js/sticky-identity)

Transformware that maintains consistent object identity when using a
[sticky](https://github.com/bvalosek/sticky) datastore.

[![browser support](https://ci.testling.com/bvalosek/sticky-identity.png)](https://ci.testling.com/bvalosek/sticky-identity)


## Installation

```
$ npm install sticky-identity
```

## Usage

Assuming we have a [sticky](https://github.com/bvalosek/sticky) `Datastore` as
`db` and some sourced repository for the `User` model:

```javascript
var identity = require('sticky-identity');

db.use(User, identity());
```

Identity is checked via the `id` parameter by default, but can be determined by
any string-like return value from a function argument:

```javascript
db.user(User, identity(function(x) { return x._id; }));
```

Keep in mind that the memory usage of this transformware will scale as the
number ofunique objects that are output or input into the repository grows.

## Testing

```
$ npm test
```

## License

MIT

