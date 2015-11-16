# MongoDB - Aula 02 - Exercício
autor: Rayllamis Almeida

## Listagem das databases (passo 2)

	> use be-mean-pokemons
	switched to db be-mean-pokemons

	> show dbs
	mean-dev          → 0.078GB
	be-mean-pokemons  → 0.078GB
	be-mean           → 0.078GB
	MEAN              → 0.078GB
	test              → 0.078GB
	node-api          → 0.078GB
	be-mean-instagram → 0.078GB
	local             → 0.078GB

## Listagem das coleções (passo 3)

	> show collections
	pokemons       → 0.001MB / 0.008MB
	system.indexes → 0.000MB / 0.008MB

## Cadastro dos pokemons (passo 4)

	> db.pokemons.insert({name: "Metapod", description: "Metapod é um pokemon tipo inseto, é a forma evoluída de Caterpie e sua próxima próxima evolução é o Butterfree", attack: 20, defense: 100, height: 7})
	Inserted 1 record(s) in 70ms
	WriteResult({
	  "nInserted": 1
	})

	> db.pokemons.insert({name: "Beedrill", description: "Evolui de Kakuna no nível 10. É a forma final de Weedle. Pode Mega Evoluir com a pedra Beedrilite", attack: 90, defense: 40, height: 10})
	Inserted 1 record(s) in 3ms
	WriteResult({
	  "nInserted": 1
	})

	> db.pokemons.insert({name: "Pidgey", description: "Pidgey é um pequeno Pokémon aviário", attack: 45, defense: 40, height: 3})
	Inserted 1 record(s) in 11ms
	WriteResult({
	  "nInserted": 1
	})

	> db.pokemons.insert({name: "Kakuna", description: "Kakuna é um pokemon tipo inseto, é a forma evoluída de Weedle e sua próxima próxima evolução é o Beedrill", attack: 25, defense: 50, height: 6})
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})

	> db.pokemons.insert({name: "Weedle", description: "Weedle o Pokémon Minhoca Espinho e do tipo Inseto e Veneno", attack: 35, defense: 30, height: 3})
	Inserted 1 record(s) in 3ms
	WriteResult({
	  "nInserted": 1
	})

## Lista dos pokemons (passo 5)

	> db.pokemons.find()
	{
	  "_id": ObjectId("5649201f3f24e66f706f2e1e"),
	  "name": "Metapod",
	  "description": "Metapod é um pokemon tipo inseto, é a forma evoluída de Caterpie e sua próxima próxima evolução é o Butterfree",
	  "attack": 20,
	  "defense": 100,
	  "height": 7
	}
	{
	  "_id": ObjectId("564920243f24e66f706f2e1f"),
	  "name": "Beedrill",
	  "description": "Evolui de Kakuna no nível 10. É a forma final de Weedle. Pode Mega Evoluir com a pedra Beedrilite",
	  "attack": 90,
	  "defense": 40,
	  "height": 10
	}
	{
	  "_id": ObjectId("5649202b3f24e66f706f2e20"),
	  "name": "Pidgey",
	  "description": "Pidgey é um pequeno Pokémon aviário",
	  "attack": 45,
	  "defense": 40,
	  "height": 3
	}
	{
	  "_id": ObjectId("5649202f3f24e66f706f2e21"),
	  "name": "Kakuna",
	  "description": "Kakuna é um pokemon tipo inseto, é a forma evoluída de Weedle e sua próxima próxima evolução é o Beedrill",
	  "attack": 25,
	  "defense": 50,
	  "height": 6
	}
	{
	  "_id": ObjectId("564920333f24e66f706f2e22"),
	  "name": "Weedle",
	  "description": "Weedle o Pokémon Minhoca Espinho e do tipo Inseto e Veneno",
	  "attack": 35,
	  "defense": 30,
	  "height": 3
	}

## Metapod (passo 6)

	> var query = {"name": "Metapod"}
	> var poke  = db.pokemons.findOne(query)
	> poke
	{
	  "_id": ObjectId("5649201f3f24e66f706f2e1e"),
	  "name": "Metapod",
	  "description": "Metapod é um pokemon tipo inseto, é a forma evoluída de Caterpie e sua próxima próxima evolução é o Butterfree",
	  "attack": 20,
	  "defense": 100,
	  "height": 7
	}

## Atualização do Metapod (passo 6)

	> poke.description = "Pokemon inseto METAFODA!"
	Pokemon inseto METAFODA!
	db.pokemons.save(poke)
	Updated 1 existing record(s) in 3ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})