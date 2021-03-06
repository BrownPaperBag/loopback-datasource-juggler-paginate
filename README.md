# loopback-datasource-juggler-paginate

Loopback Datasource Juggler plugin that adds `findPaginate` method to Model.

Currently expects query params as given by [`ng-table`][1], and provides an object intended to be used by the same.

## Usage

```JavaScript
Model = connection.define('models', {
 title: String,
 status: {
   type: String,
   default: 'Active'
 },
 created: {
   type: Date,
   default: Date.now
 },
 updated: Date
});
  
loopbackPaginate.addPaginateFunction(Model);

/**
  *
  * @param {Object} Query params
  * @param {[Object]} Optional query to be lodash.extend'ed onto the pagination query
  * @return {Promise}
  */
Model.findPaginate(req.query, {
  where: {
    status: {
      neq: 'Deleted'
    }
  }
}).then(function(models) {
  console.log(models);
});
```

[1]: https://github.com/esvit/ng-table
