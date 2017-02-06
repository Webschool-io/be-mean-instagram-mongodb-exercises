```js
root@blsrocks:/home/blsrocks/be-mean-instagram# mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json 
2016-08-13T14:10:56.978-0300	connected to: localhost
2016-08-13T14:10:56.994-0300	dropping: be-mean.restaurantes
2016-08-13T14:10:58.959-0300	imported 25359 documents

blsrocks(mongod-3.2.8) be-mean> db.restaurantes.find({}).count()
25359
```