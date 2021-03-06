Node Parse API
==============

install
-------

    npm install node-parse-api

examples
--------

### setup

    var Parse = require('parse-api').Parse;
    
    var APP_ID = ...;
    var MASTER_KEY = ...;
    
    var app = new Parse(APP_ID, MASTER_KEY);

### insert

    // add a Foo object, { foo: 'bar' }
    app.insert('Foo', { foo: 'bar' }, function (err, response) {
      console.log(response);
    });

### insert a file

    app.insertFile(fileName, data, fileType, function (err, response) {
      fileLink = response.url;
      parseName = response.name;
        app.insert('Foo', { "foo" : fileLink, "bar" : parseName }, function(erro, res){
       })
    });

### find one

    // the Foo with id = 'someId'
    app.find('Foo', 'someId', function (err, response) {
      console.log(response);
    });

### find many

    // all Foo objects with foo = 'bar'
    app.findMany('Foo', { foo: 'bar' }, function (err, response) {
      console.log(response);
    });

### update

    app.update('Foo', 'someId', { foo: 'fubar' }, function (err, response) {
      console.log(response);
    });

### delete

    app.delete('Foo', 'someId', function (err) {
      // nothing to see here
    });

### reset a password

    //email is built into Parse's special User class 
    app.passwordReset(email, function(err, response){
      console.log(response);
    });

### update User email

    //email is built into Parse's special User class 
    app.updateUserEmail(objectId, email, function(err, response){
      if (err) {
        console.log(err);
      } else {
        console.log(response);
      }
    });

### insert installation data

    //first arg is either 'ios' or 'android'.  second arg is either the Apple deviceToken or the Android installationId.  The other args are optional
    app.insertInstallationData("ios", "0123456784abcdef0123456789abcdef0123456789abcdef0123456789abcdef", function(err, response){
      if (err) {
        console.log(err);
      } else {
        console.log(response);
      }
    });