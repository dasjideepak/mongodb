#### write commands for following mongodb opertaions

1. create a database named `sports`
```js
  use sports
```

2. list all databases present in local mongod server.
```js
  admin    0.000GB
  config   0.000GB
  local    0.000GB
```

3. create 3 collections named `cricket`, `football`, `TT` in sports database.
```js
  > db.createCollection('cricket')
  > db.createCollection("football");
  > db.createCollection("TT");
```

4. add 3 players in each of above collections which should have fields like `name`, `age`, `email`, state and auction_price.
```js
  > db.football.insertMany([{"name":"deepak", "age":"18", "email":"dasjideepak@gmail.com"}, {"name":"vishnu", "age":"19", "email":"vishnu@gmail.com"}, {"name":"shivam", "age":"16", "email":"shivam@gmail.com"}]);
  > db.cricket.insertMany([{"name":"sachin", "age":"48", "email":"sachin@gmail.com"}, {"name":"Dhoni", "age":"50", "email":"dhoni@gmail.com"}, {"name":"Rohit", "age":"35", "email":"rohit@gmail.com"}]);
  > db.TT.insertMany([{"name":"apporv", "age":"21", "email":"apporv@gmail.com"}, {"name":"Ashish", "age":"24", "email":"ashish@gmail.com"}, {"name":"Naveen", "age":"26", "email":"naveen@gmail.com"}]);
```

5. list all collections in sports database.
```js
  > db.getCollectionNames();
    [ "football", "TT", "cricket" ]
```

6. rename `TT` collection to `tennis`.
```js
  > db.TT.renameCollection("tennis");
```

7. create a capped collection called `khokho` which should have max 3 documents.
  Try inserting more than 3 and output the result here ?
```js
  > db.createCollection("khokho", {capped: true, size: 1000, max: 3});
```

8. check whether a collection is capped or not?
```js
  //  Yes, Capped
```

9. remove all documents from `football` collection.
```js
  > db.football.remove({});
```

10. delete cricket collection completely.
```js
  >  db.cricket.drop();
```

11. rename database sports to games
```js
// Unable to do it
```

12. delete sports database. 
```js
  > db.dropDatabase();
```