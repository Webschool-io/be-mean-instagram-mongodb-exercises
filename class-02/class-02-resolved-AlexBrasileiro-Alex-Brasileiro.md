```

	use be-mean-pokemons
	switched to db be-mean-pokemons


```

```

	show dbs
	be-mean-instagram → 0.078GB
	be-mean           → 0.078GB
	local             → 0.078GB
	test              → 0.078GB

```

```

	show collections
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> 

```

```

	db.pokemons.find()
	{
		"_id": ObjectId("5679ed9f021db0d38f00d9fe"),
		"name": "Ivysaur",
		"description": "Ivysaur's legs and trunk grow thick and strong",
		"attack": 4,
		"defense": 3,
		"height": 1
	}
	{
		"_id": ObjectId("5679ed9f021db0d38f00d9ff"),
		"name": "Wartortle",
		"description": "Its tail is large and covered with a rich, thick fur",
		"attack": 3,
		"defense": 4,
		"height": 1
	}
	{
		"_id": ObjectId("5679ed9f021db0d38f00da00"),
		"name": "Kakuna",
		"description": "Kakuna remains virtually immobile as it clings to a tree",
		"attack": 1,
		"defense": 2,
		"height": 0.6
	}
	{
		"_id": ObjectId("5679ed9f021db0d38f00da01"),
		"name": "Blastoise",
		"description": "Blastoise has water spouts that protrude from its shell",
		"attack": 4,
		"defense": 4,
		"height": 1.6
	}
	{
		"_id": ObjectId("5679ed9f021db0d38f00da02"),
		"name": "Sandshrew",
		"description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert",
		"attack": 4,
		"defense": 4,
		"height": 0.6
	}
	Fetched 5 record(s) in 2ms 

```

```

	var query = {name: 'Kakuna'}
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)

```

```

	poke.description = 'Descrição Modificada - Ele é feinho que dói!'
	Descrição Modificada - Ele é feinho que dói!
	
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> poke
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da00"),
	  "name": "Kakuna",
	  "description": "Descrição Modificada - Ele é feinho que dói!",
	  "attack": 1,
	  "defense": 2,
	  "height": 0.6
	}
	
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> db.pokemons.save(poke)
	Updated 1 existing record(s) in 4ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> db.pokemons.find()
	{
	  "_id": ObjectId("5679ed9f021db0d38f00d9fe"),
	  "name": "Ivysaur",
	  "description": "Ivysaur's legs and trunk grow thick and strong",
	  "attack": 4,
	  "defense": 3,
	  "height": 1
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00d9ff"),
	  "name": "Wartortle",
	  "description": "Its tail is large and covered with a rich, thick fur",
	  "attack": 3,
	  "defense": 4,
	  "height": 1
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da00"),
	  "name": "Kakuna",
	  "description": "Descrição Modificada - Ele é feinho que dói!",
	  "attack": 1,
	  "defense": 2,
	  "height": 0.6
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da01"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell",
	  "attack": 4,
	  "defense": 4,
	  "height": 1.6
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da02"),
	  "name": "Sandshrew",
	  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert",
	  "attack": 4,
	  "defense": 4,
	  "height": 0.6
	}
	Fetched 5 record(s) in 2ms


```