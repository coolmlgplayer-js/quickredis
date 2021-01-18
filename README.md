# quickredis-db
Quick Redis is a wrapper for the [redis](https://npmjs.com/package/redis) package similar to quick.db.

Quick Redis is promise based and currently features the following commands:
* get
* set
* add
* subtract
* delete

Example code:

```js
const redis = require('quickredis-db');
const client = redis.createClient();

client.once('ready', () => console.log('Connected to redis database'));

// Setting a value
client.set('foo', 'bar').then(console.log); // Will log 'bar' to console (logs whatever gets set)

// Reading a value
client.get('foo').then(console.log); // Will log 'bar' to console

// Setting a value using dotted notation
client.set('foo.bar', 'baz').then(console.log); // Will log { bar: 'baz' } to console

// Reading a value using dotted notation
client.get('foo.bar').then(console.log); // Will log 'baz' to console

client.get('foo').then(console.log); // Will log { bar: 'baz' } to console

// Using add and subtract
client.set('foo', 1).then(console.log); // Will log 1 to console

client.add('foo', 5).then(console.log); // Will log 6 to console and add 5 to the value of foo

client.subtract('foo', 1).then(console.log); // Will log 5 to console and subtract 1 from the value of foo

client.get('foo').then(console.log); // Will log 5 to console

```