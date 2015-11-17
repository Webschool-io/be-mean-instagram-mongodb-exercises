# MongoDB - Aula 02 - Exercício
autor: Joao Siqueira

## Criar a database be-mean-pokemons

    ```
    	mongo be-mean-pokemons
	MongoDB shell version: 2.6.10
	connecting to: be-mean-pokemons
	Mongo-Hacker 0.0.8

    ```

## Listar os databases

    ```
	    show dbs
	be-mean-instagram → 0.078GB
	be-mean           → 0.078GB
	test              → 0.078GB
	local             → 0.078GB
	admin             → (empty)


    ```

## Listar as colections do database
	```
	joao-Vostro-5470(mongod-2.6.10) test> show collections

	```

## Inserir 5 pokemons no padrão: name, description, attack, defense e height
	```
	var pokemons = [{'name': 'Charizard', 'description':'Pokemão foda', 'type': 'fogo', 'attack':84, 'defense':78, 'height':1.70}, {'name':'Alakazam','description': 'QI de 9000, mas nao fala 2 palavras', 'type':'Psychic', 'attack':50, 'defense':45, 'height':1.50}, {'name': 'Rayquaza', 'description':'Lagartão que avua', 'type':'dragon/fly', 'attack':150, 'defense':90, 'height':7.001}, {'name':'Pidgeot', 'description':'Baita de uma ave, digassi de passagi', 'type':'normal/fly', 'attack':80, 'defense':75, 'height':1.50}, {'name':'Ninetales', 'description':'Cachorrão lindo','type':'fire', 'attack':76, 'defense':75, 'height':1.09}]


	joao-Vostro-5470(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(pokemons)
	Inserted 1 record(s) in 59ms
	BulkWriteResult({
	  "writeErrors": [ ],
	  "writeConcernErrors": [ ],
	  "nInserted": 5,
	  "nUpserted": 0,
	  "nMatched": 0,
	  "nModified": 0,
	  "nRemoved": 0,
	  "upserted": [ ]


## Busque o pokemon a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;
	```
	var pokemon = {'name':'Charizard'}
	var poke = db.pokemons.findOne(pokemon)

	
		{
	  "_id": ObjectId("5645554a40e9fbb07dd1c3c4"),
	  "name": "Charizard",
	  "description": "Pokemão foda",
	  "type": "fogo",
	  "attack": 84,
	  "defense": 78,
	  "height": 1.7
	}

	```

## Modifique sua `description` e salvê-o
	```
	 	poke.description = 'Avoa e cospe fogo? C é o bixão memo hein'
 
		db.pokemons.save(poke);

	
	Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

	```
