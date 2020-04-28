1. Create a database named `blog`.
```js
  > use blog
```

2. Create a collection called 'articles'.
```js
  > db.createCollection("articles")
```

3. Insert multiple documents(at least 3) into articles. It should have fields
```js
   db.articles.insert([{"title":"HTML", "description":"HTML stands for HyperText Markup Language", 'author':{'name': 'abc', 'email': 'abc@gmail', 'age': 25}, 'tags':['html', 'web' ,'htm']}])
   db.articles.insert([{"title":"CSS", "description":"Cascading Stylesheet", 'author':{'name': 'xyz', 'email': 'xyz@gmail', 'age': 21}, 'tags':['css', 'style' ,'design']}])
   db.articles.insert([{"title":"JS", "description":"JavaScript is a Scripting Language", 'author':{'name': 'das', 'email': 'das@gmail.com', 'age': 19}, 'tags':['node', 'javascript' ,'js']}])
```

4. Find all the articles using `db.COLLECTION_NAME.find()`
```js
  > db.articles.find()
    { "_id" : ObjectId("5ea7119b054c647bdd2ef4a3"), "title" : "HTML", "description" : "HTML stands for HyperText Markup Language", "author" : { "name" : "abc", "email" : "abc@gmail", "age" : 25 }, "tags" : [ "html", "web", "htm" ] }
    { "_id" : ObjectId("5ea71267054c647bdd2ef4a4"), "title" : "CSS", "description" : "Cascading Stylesheet", "author" : { "name" : "xyz", "email" : "xyz@gmail", "age" : 21 }, "tags" : [ "css", "style", "design" ] }
    { "_id" : ObjectId("5ea7136d054c647bdd2ef4a5"), "title" : "JS", "description" : "JavaScript is a Scripting Language", "author" : { "name" : "das", "email" : "das@gmail", "age" : 18 }, "tags" : [ "node", "javascript", "js" ] }
```

5. Find a document using _id field.
```js
  > db.articles.find({"_id" : ObjectId("5ea7119b054c647bdd2ef4a3")})
```

6. Find documents using title and author's name field.
```js
  > db.articles.find({}, {title:"", 'author.name':''})
```

7. Find document using a specific tag.
```js
  > db.articles.find({tags:"html"})
```

8. Update title of a document using its _id field.
```js
  > db.articles.update({"_id":ObjectId("5ea85f08d665e1a08b806230")}, {$set: {title:"Markup"}})
```

9. Update a author's name using article's title.
```js
  > db.articles.update({"title":"Markup"}, {$set: {author:{name:"deepak"}}});
```

10. rename details field to description from articles collection. 
```js
  > db.articles.update({}, {$rename: {'description':'details'}})
```

11. Add additional tag in a specific document.
```js
> db.articles.update({"title":"Markup"}, {$push: {tags: "deepak"}});
```

12. Update an article's tags using $set and without $set.
  - Write the differences here ?
```js
  > db.articles.update({"title":"Markup"}, {$set: {tags: ['internet', 'web', 'net'}});
```

13. Increment an auhtor's age by 5.  
```js
  > db.articles.update({'title':'Markup'}, {$inc: {'author.age': 5}})
```

14. Delete a document using _id field with `db.COLLECTION_NAME.remove()`.
```js
  db.articles.remove({"title" : "CSS"})
```

Use sample.js data for below queries.

1. Find all males who play cricket.
```js
db.users.find()
> db.users.find({'gender': 'Male'}, {'sports':'cricket'})
```

2. Update user with extra golf field in sports array whose name is "Steve Ortega".
```js
  > db.users.update({'name':'Steve Ortega'}, {$push: {sports:'golf'}});
```

3. Find all users who play either 'football' or 'cricket'.
```js
  > db.users.find({'sports':'cricket'}, {'sports':'football'});
```

4. Find all users whose name includes 'ri' in their name.
```js
db.users.find({name:ri/i})
```