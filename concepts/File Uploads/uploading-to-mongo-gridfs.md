# Uploading to Mongo GridFS

Uploading files to MongoDB is possible thanks to Mongo's GridFS filesystem.  With Sails, you can accomplish this with very little additional configuration using the Skipper adapter for [MongoDB's GridFS](https://github.com/willhuang85/skipper-gridfs).

Install it with:

```sh
$ npm install skipper-gridfs --save
```

Then use it in one of your controllers:

```javascript
  uploadFile: function (req, res) {
    req.file('avatar').upload({
      adapter: require('skipper-gridfs'),
      uri: 'mongodb://[username:password@]host1[:port1][/[database[.bucket]]'
    }, function (err, filesUploaded) {
      if (err) return res.serverError(err);
      return res.ok();
    });
  }
```
As of skipper-gridfs@0.5.3 the adapter does not currently support Node versions >= v4.0.
<docmeta name="displayName" value="Uploading to GridFS">
