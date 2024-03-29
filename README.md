# Routie

Routie is a javascript hash routing library.  It is designed for scenarios when push state is not an option (IE8 support, static/Github pages, Phonegap, simple sites, etc). It is very tiny (800 bytes gzipped), and should be able to handle all your routing needs.

## Download

- [Source](https://github.com/jgallen23/routie)

## Basic Usage

There are three ways to call routie:

Here is the most basic way:

```js
routie('users', function() {
  //this gets called when hash == #users
});
```

If you want to define multiple routes you can pass in an object like this:

```js
routie({
  'users': function() {

  },
  'about': function() {
  }
});
```

If you want to trigger a route manually, you can call routie like this:

```js
routie('users/bob');  //window.location.hash will be #users/bob
```

## Regex Routes

Routie also supports regex style routes, so you can do advanced routing like this:

```js
routie('users/:name', function(name) {
  //name == 'bob';
});
routie('users/bob');
```

### Optional Params:
```js
routie('users/:name?', function(name) {
  //name == undefined
  //then
  //name == bob
});
routie('users/');
routie('users/bob');
```

### Wildcard:
```js
routie('users/*', function() {
});
routie('users/12312312');
```

### Catch All:
```js
routie('*', function() {
});
routie('anything');
```

## Named Routes

Named routes make it easy to build urls for use in your templates.  Instead of re-creating the url, you can just name your url when you define it and then perform a lookup.  The name of the route is optional.  The syntax is "\[name\] \[route\]".

```js
routie('user users/:name', function() {});
```

then in your template code, you can do:

```js
routie.lookup('user', { name: 'bob'}) // == users/bob
```


## Dependencies

None

## Supports

Any modern browser and IE8+

## Tests

Run `make install`, then `make test`, then go to http://localhost:8000/test
