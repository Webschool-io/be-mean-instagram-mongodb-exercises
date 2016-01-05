1. Liste todos Pokemons com a altura menor que 0.5;
2. Liste todos Pokemons com a altura maior ou igual que 0.5;
3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;


1. Liste todos Pokemons com a altura menor que 0.5;

```

	var query = {height : {$lt : 0.5}}
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> query
	{
	  "height": {
	    "$lt": 0.5
	  }
	}
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms
	

```

2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```

	var query = {height : {$gte : 0.5}}
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> query
	{
	  "height": {
	    "$gte": 0.5
	  }
	}
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
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
	Fetched 5 record(s) in 6ms


```

3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```

	var query = {
	... 
	... $and: [
	... { height : {$lte : 0.5} },
	... { type : 'grama'}
	... ]
	... 
	... }
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "height": {
	        "$lte": 0.5
	      }
	    },
	    {
	      "type": "grama"
	    }
	  ]
	}
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms


```

4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
	
	var query = {
	... 
	... $or: [
	... { name : 'Pikachu' },
	... { attack : {$lte : 0.5}}
	... ]
	... 
	... }
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> query
	{
	  "$or": [
	    {
	      "name": "Pikachu"
	    },
	    {
	      "attack": {
	        "$lte": 0.5
	      }
	    }
	  ]
	}
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms


```

5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```

	var query = {
	... 
	... $and: [
	... { attack : {$gte : 48}},
	... { heigth : {$lte : 0.5}}
	... ]
	... 
	... }
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "attack": {
	        "$gte": 48
	      }
	    },
	    {
	      "heigth": {
	        "$lte": 0.5
	      }
	    }
	  ]
	}
	MacBook-Pro-de-Alex(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms


```
