# MongoDB - Aula 02 - Exercício
**Autor:** Helton Barbosa

## 1ª Questão 
### Crie uma database chamada be-mean-pokemons;

MongoDB não fornece qualquer comando para criar "banco de dados".
Na verdade, o MangoDB irá criá-lo em tempo real, durante a primeira vez em que for salvo um documento JSON.
A criação ocorrerar de fato na 4ª questão.
	
## 2ª Questão
### Liste quais databases você possui nesse servidor;

```
helton@mongodb:~$ mongo be-mean-pokemons
MongoDB shell version: 3.0.7
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.8
mongodb(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean           → 0.078GB
local             → 0.078GB
be-mean-instagram → 0.078GB
test              → 0.078GB
```

## 3ª Questão
### Liste quais coleções você possui nessa database;

```
mongodb(mongod-3.0.7) be-mean-pokemons> show collections
mongodb(mongod-3.0.7) be-mean-pokemons>
```
    
## 4 ª Questão
### Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name,description, attack, defense e height;

```
helton@mongodb:~$ mongoimport --db be-mean-pokemons --collection pokemons --file pokemons.json
2015-11-19T10:05:24.529-0300    connected to: localhost
2015-11-19T10:05:24.727-0300    imported 9 documents
```
    
## 5ª Questão
### Liste os pokemons existentes na sua coleção;

```
mongodb(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{"_id": ObjectId("564dc914b0266c6edfc33203"), "name": "Pikachu", "description": "Rato elétrico bem fofinho", "type": "electric", "attack": 55, "height": 0.4}
{"_id": ObjectId("564dc914b0266c6edfc33204"), "name": "Bulbassauro", "description": "Chicote de trepadeira", "type": "grama", "attack": 49, "height": 0.4}
{"_id": ObjectId("564dc914b0266c6edfc33205"), "name": "Squirtle", "description": "Ejeta água que passarinho não bebe", "type": "água", "attack": 48, "height": 0.5}
{"_id": ObjectId("564dc914b0266c6edfc33206"), "name": "Caterpie", "description": "Larva lutadora", "type": "inseto", "attack": 30, "height": 0.3}
{"_id": ObjectId("564dc914b0266c6edfc33207"), "name": "Ferrothorn", "description": "By swinging around its three spiky feelers and shooting spikes, it can obliterate an opponent.", "type": "grama", "attack": 50, "height": 1}
{"_id": ObjectId("564dc914b0266c6edfc33208"), "name": "Fraxure", "description": "Their tusks can shatter rocks. Territory battles between Fraxure can be intensely violent.", "type": "dragao", "attack": 68, "height": 1}
{"_id": ObjectId("564dc914b0266c6edfc33209"), "name": "Fearow", "description": "Fearow is recognized by its long neck and elongated beak. They are conveniently shaped for catching prey in soil or water. It deftly moves its long and skinny beak to pluck prey.", "type": "normal", "attack": 47, "height": 1.2}
{"_id": ObjectId("564dc914b0266c6edfc3320a"), "name": "Haunter", "description": "Haunter is a dangerous Pokémon. If one beckons you while floating in darkness, you must never approach it. This Pokémon will try to lick you with its tongue and steal your life away.", "type": "fantasma", "attack": 32, "height": 1.6}
{"_id": ObjectId("564dc914b0266c6edfc3320b"), "name": "Voltorb", "description": "Voltorb was first sighted at a company that manufactures Poké Balls. The link between that sighting and the fact that this Pokémon looks very similar to a Poké Ball remains a mystery.", "type": "eletrico", "attack": 20, "height": 0.5}
Fetched 9 record(s) in 98ms
```
## 6ª Questão
### Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada "pokemon";

```
mongodb(mongod-3.0.7) be-mean-pokemons> var query = {"name": "Fraxure"}
mongodb(mongod-3.0.7) be-mean-pokemons> var pokemon = db.pokemons.findOne(query)
mongodb(mongod-3.0.7) be-mean-pokemons> pokemon
	{
		"_id": ObjectId("564dc914b0266c6edfc33208"),
		"name": "Fraxure",
		"description": "Their tusks can shatter rocks. Territory battles between Fraxure can be intensely violent.",
		"type": "dragao",
		"attack": 68,
		"height": 1
	}
```

## 7ª Questão
### Modifique sua "description" e salve-o;

```
mongodb(mongod-3.0.7) be-mean-pokemons> pokemon.description = "Suas presas podem quebrar rochas."
Suas presas podem quebrar rochas.
mongodb(mongod-3.0.7) be-mean-pokemons> pokemon
	{
		"_id": ObjectId("564dc914b0266c6edfc33208"),
		"name": "Fraxure",
		"description": "Suas presas podem quebrar rochas.",
		"type": "dragao",
		"attack": 68,
		"height": 1
	}
mongodb(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
	Updated 1 existing record(s) in 24ms
	WriteResult({
		"nMatched": 1,
		"nUpserted": 0,
		"nModified": 1
	})
```


 


