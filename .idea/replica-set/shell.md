## mongo shell

### 1. shell connect
````text
mongosh "mongodb://localhost:27017"
````

### 2. check replica set
````text
rs.status()
````

### 3. replica init
````text
rs.initiate({
    _id: "rs1",
    members: [
        { _id: 0, host: "localhost:27017" },
        { _id: 1, host: "localhost:27018" },
        { _id: 2, host: "localhost:27019" },
    ],
});
````