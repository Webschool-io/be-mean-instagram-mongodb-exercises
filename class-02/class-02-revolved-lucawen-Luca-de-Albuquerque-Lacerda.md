# MongoDB - Aula 02 - Exercício
autor: Luca Albuquerque

## Crie uma database chamada be-mean-pokemons;


    ```
	> use be-mean-pokemons
	switched to db be-mean-pokemons
    ```

## Liste quais databases você possui nesse servidor;

    ```
    > show dbs
	admin             → (empty)
	be-mean           → 0.078GB
	be-mean-instagram → 0.078GB
	local             → 0.078GB
	sortearme         → 0.078GB
    ```
	
## Liste quais coleções você possui nessa database;

    ```
    > show collections
	
    ```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

	```
    > var pokemon = {'name':'Charmander','description':'The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.','type': 'Lizard', attack: 30, height: 0.6, defense: 20 }
	> db.pokemons.save(pokemon);
	Inserted 1 record(s) in 0ms
	WriteResult({
	  "nInserted": 1
	})
    ```
	
	```
    > var pokemon = {'name':'Squirtle','description':'Squirtle shell is not merely used for protection. The shell rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.','type': 'Tiny Turtle', attack: 30, height: 0.5, defense: 30 }
	> db.pokemons.save(pokemon);
	Inserted 1 record(s) in 44ms
	WriteResult({
	  "nInserted": 1
	})
    ```
	
	```
	> var pokemon = {'name':'Bulbasaur','description':'Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun rays, the seed grows progressively larger.','type': 'Seed', attack: 30, height: 0.7, defense: 20 }
	> db.pokemons.save(pokemon);
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
    ```
	
	```
    > var pokemon = {'name':'Blastoise ','description':'Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.','type': 'EspécieShellfish', attack: 40, height: 1.6, defense: 40 }
	> db.pokemons.save(pokemon);
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
    ```
	
	```
	> var pokemon = {'name':'Charmeleon','description':'Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.','type': 'Flame', attack: 30, height: 1.1, defense: 30}
	> db.pokemons.save(pokemon);
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
    ```
	
## Liste os pokemons existentes na sua coleção;
	
	```
	> db.pokemons.find()
	{
	  "_id": ObjectId("56bf7c8ff12655fa0d10a264"),
	  "name": "Squirtle",
	  "description": "Squirtle shell is not merely used for protection. The shell rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
	  "type": "Tiny Turtle",
	  "attack": 30,
	  "height": 0.5,
	  "defense": 30
	}
	{
	  "_id": ObjectId("56bf7d0ef12655fa0d10a265"),
	  "name": "Bulbasaur",
	  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun rays, the seed grows progressively larger.",
	  "type": "Seed",
	  "attack": 30,
	  "height": 0.7,
	  "defense": 20
	}
	{
	  "_id": ObjectId("56bf7d2ff12655fa0d10a266"),
	  "name": "Blastoise ",
	  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
	  "type": "EspécieShellfish",
	  "attack": 40,
	  "height": 1.6,
	  "defense": 40
	}
	{
	  "_id": ObjectId("56bf7d91f12655fa0d10a267"),
	  "name": "Charmander",
	  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
	  "type": "Lizard",
	  "attack": 30,
	  "height": 0.6,
	  "defense": 20
	}
	{
	  "_id": ObjectId("56bf7e21f12655fa0d10a268"),
	  "name": "Charmeleon",
	  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
	  "type": "Flame",
	  "attack": 30,
	  "height": 1.1,
	  "defense": 30
	}
	Fetched 5 record(s) in 7ms
    ```
	
## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

	```
	> var query = {"name": "Charmander"}
	> var poke = db.pokemons.findOne(query)
	```
	
## Modifique sua `description` e salvê-o.

	```
	> poke.description = "Um carinha que pega fogo"
	Um carinha que pega fogo
	> db.pokemons.save(poke)
	Updated 1 existing record(s) in 1ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	```

	

	












