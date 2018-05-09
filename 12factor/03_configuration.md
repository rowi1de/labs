# 3 - Configuration

Configuration (credentials, database connection string, ...) should be stored in the environment.

## What does that mean for our application ?

In _config/datastores.js_, we change the _default_ datastore and use MONGO_URL environment variable to pass the mongo connection string.

```node
module.exports.datastores = {
  default: {
    adapter: 'sails-mongo',
    url: process.env.MONGO_URL
  }
};
```

In _config/model.js_, we make sure the _mongodb_ compatible _id_ is defined.

```node
module.exports.models = {
  migrate: 'alter',
  attributes: {
    // id: { type: 'number', autoIncrement: true, },
    id: { type: 'string', columnName: '_id' },
    //...
    }
};
```

Those changes enable to provide a different _MONGO_URL_ very easily as it's defined in the environment.

[Previous](02_dependencies.md) - [Next ](04_external_services.md)
