```

	mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
	2015-12-22T19:54:03.216-0200	connected to: 127.0.0.1
	2015-12-22T19:54:03.217-0200	dropping: be-mean.restaurantes
	2015-12-22T19:54:04.504-0200	imported 25359 documents

```

```

	db.restaurantes.find({}).count()
	25359

```