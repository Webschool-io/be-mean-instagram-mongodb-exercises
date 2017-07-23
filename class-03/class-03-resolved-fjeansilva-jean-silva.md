# MongoDB - Aula 03 - Exercício
autor: Jean Silva

## Selecionando o database (passo 1)
	
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) teste> use be-mean-pokemons
	switched to db be-mean-pokemons

## Listagem todos os documentos existentes na collection pokemons (passo 2)

	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find();
	{
	  "_id": ObjectId("5643515c87a2096df79637b9"),
	  "name": "Charizard",
	  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
	  "attack": 5,
	  "defense": 3,
	  "height": 1.7,
	  "type": "Fire"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637ba"),
	  "name": "Squirtle",
	  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
	  "attack": 2,
	  "defense": 35,
	  "height": 0.5,
	  "type": "Water"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637bb"),
	  "name": "Wartortle",
	  "description": "Its tail is large and covered with a rich, thick fur. The tail becomes increasingly deeper in color as Wartortle ages. The scratches on its shell are evidence of this Pokémon's toughness as a battler.",
	  "attack": 3,
	  "defense": 4,
	  "height": 1,
	  "type": "Water"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637bc"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
	  "attack": 4,
	  "defense": 4,
	  "height": 0.4,
	  "type": "Grass"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637bd"),
	  "name": "Butterfree",
	  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
	  "attack": 4,
	  "defense": 2,
	  "height": 1.1,
	  "type": "Flying"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637be"),
	  "name": "Pikachu",
	  "description": "Description Pikachu Update",
	  "attack": 3,
	  "defense": 2,
	  "height": 0.4,
	  "type": "Electric"
	}
	Fetched 6 record(s) in 3ms

## Listagem de todos os pokemons com altura menor que 0.5 (passo 3)

	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { height: { $lt: 0.5 } }
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
	{
	  "height": {
	    "$lt": 0.5
	  }
	}
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
	{
	  "_id": ObjectId("5643515c87a2096df79637bc"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
	  "attack": 4,
	  "defense": 4,
	  "height": 0.4,
	  "type": "Grass"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637be"),
	  "name": "Pikachu",
	  "description": "Description Pikachu Update",
	  "attack": 3,
	  "defense": 2,
	  "height": 0.4,
	  "type": "Electric"
	}
	Fetched 2 record(s) in 2ms

## Listagem de todos os pokemons com altura maior ou igual que 0.5 (passo 4)

	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { height: { $gte: 0.5 } }
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
	{
	  "height": {
	    "$gte": 0.5
	  }
	}
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
	{
	  "_id": ObjectId("5643515c87a2096df79637b9"),
	  "name": "Charizard",
	  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
	  "attack": 5,
	  "defense": 3,
	  "height": 1.7,
	  "type": "Fire"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637ba"),
	  "name": "Squirtle",
	  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
	  "attack": 2,
	  "defense": 35,
	  "height": 0.5,
	  "type": "Water"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637bb"),
	  "name": "Wartortle",
	  "description": "Its tail is large and covered with a rich, thick fur. The tail becomes increasingly deeper in color as Wartortle ages. The scratches on its shell are evidence of this Pokémon's toughness as a battler.",
	  "attack": 3,
	  "defense": 4,
	  "height": 1,
	  "type": "Water"
	}
	{
	  "_id": ObjectId("5643515c87a2096df79637bd"),
	  "name": "Butterfree",
	  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
	  "attack": 4,
	  "defense": 2,
	  "height": 1.1,
	  "type": "Flying"
	}
	Fetched 4 record(s) in 2ms

## Listagem de todos os pokemons com altura menor ou igual que 0.5 e do tipo grama (passo 5)

	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { height: { $lte: 0.5 } }, { type: 'Grass' } ] }
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "height": {
	        "$lte": 0.5
	      }
	    },
	    {
	      "type": "Grass"
	    }
	  ]
	}
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
	{
	  "_id": ObjectId("5643515c87a2096df79637bc"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
	  "attack": 4,
	  "defense": 4,
	  "height": 0.4,
	  "type": "Grass"
	}
	Fetched 1 record(s) in 2ms

## Listagem de todos os pokemons com name 'Pikachu' ou com attack menor ou igual que 0.5 (passo 6)

	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { $or: [ { name: 'Pikachu' }, { attack: { $lte: 0.5 } } ] }
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
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
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
	{
	  "_id": ObjectId("5643515c87a2096df79637be"),
	  "name": "Pikachu",
	  "description": "Description Pikachu Update",
	  "attack": 3,
	  "defense": 2,
	  "height": 0.4,
	  "type": "Electric"
	}
	Fetched 1 record(s) in 1ms

## Listagem de todos os pokemons com attack maior ou igual que 48 e height menor ou igual que 0.5 (passo 7)

	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { attack: { $gte: 48 } }, { height: { $lte: 0.5 } } ] }
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "attack": {
	        "$gte": 48
	      }
	    },
	    {
	      "height": {
	        "$lte": 0.5
	      }
	    }
	  ]
	}
	Jean-Silvas-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
	Fetched 0 record(s) in 1ms