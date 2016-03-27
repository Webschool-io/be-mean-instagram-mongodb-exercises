#MongoDB - Aula 02 - Exercício
autor: Joao Antonio Gardin Vieira

##Criando a database
```
be-mean-instagram-mongodb-exercises$ mongo be-mean-instagram
```

##Listagem das databases 
```
be-mean-pokemons> show dbs
be-mean           → 0.008GB
be-mean-instagram → 0.000GB
database          → 0.004GB
local             → 0.000GB
restaurantes      → 0.004GB
test              → 0.000GB
```

##Listagem das coleções
```
be-mean-instagram> show collections
pokemons → 0.001MB / 0.035MB
test     → 0.000MB / 0.031MB
```

##Adicionando pokemons a coleção
```
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {'name': 'Weedle', 'description': 'Este pokemon possui o poder de sexto sentido', 'type': 'bug', 'attack': 35, 'heigth': 0.3, 'defese': 30 };
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {"name": "pidgey", 'description': 'Pokemon voador com geolocalizador', 'type': 'flying', 'attack': 45 , 'heigth': 0.3, 'defese': 40 };
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {"name": "Rattata", 'description': 'Pokemon comedor de queijo', 'type': 'normal', 'attack': 56, 'heigth': 0.3, 'defese': 35 };
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {"name": "Spearow", 'description': 'Spearow tem um grito muito alto que pode ser ouvido mais de meia milha de distância', 'type': 'flying', 'attack': 60, 'heigth': 0.3, 'defese': 30};
Tto(mongod-3.2.1) be-mean-instagram> 
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {"name": "Ekans", 'description': 'Ekans enrola-se em uma espiral enquanto descansa', 'type': 'snake', 'attack': 60, 'heigth': 2.0, 'defese': 44  };
Tto(mongod-3.2.1) be-mean-instagram> 
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Tto(mongod-3.2.1) be-mean-instagram> 
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {"name": "vulpix", 'description': 'Na época de seu nascimento, Vulpix tem uma cauda branca.', 'type': 'fire', 'attack': 40, 'heigth': 0.6, 'defese': 41};
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {"name": "Venonat", 'description': 'Venonat é dito ter evoluído com um casaco de cabelo fino', 'type': 'poison', 'attack': 55, 'heigth': 1.0, 'defese': 50};
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {"name": "Meowth", 'description': 'este Pokémon ama moedas brilhantes que brilham com a luz.', 'type': 'normal', 'attack': 45, 'heigth': 0.4 , 'defese': 35};
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = {"name": "Mankey", 'description': ' é impossível para qualquer um de fugir a sua ira.', 'type': 'figthing', 'attack': 80, 'heigth': 0.5 , 'defese': 40};
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```

## Listando os pokemons cadastrados
```
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.find({})
{
  "_id": ObjectId("56b96ff113858fed541cda5b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "heigth": 0.4
}
{
  "_id": ObjectId("56b9702813858fed541cda5c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "heigth": 0.4
}
{
  "_id": ObjectId("56b9704813858fed541cda5d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "heigth": 0.6
}
{
  "_id": ObjectId("56b9706c13858fed541cda5e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinhoo não bebe",
  "type": "água",
  "attack": 48,
  "heigth": 0.5
}
{
  "_id": ObjectId("56b972bb9c6d5acc1f92e9d9"),
  "name": "Caterpie",
  "description": "Larva lutadore",
  "type": "inseto",
  "attack": 30,
  "heigth": 0.3,
  "defese": 35
}
{
  "_id": ObjectId("56b97c7c4f203473d0d38d41"),
  "name": "Weedle",
  "description": "Este pokemon possui o poder de sexto sentido",
  "type": "bug",
  "attack": 35,
  "heigth": 0.3,
  "defese": 30
}
{
  "_id": ObjectId("56b97c834f203473d0d38d42"),
  "name": "pidgey",
  "description": "Pokemon voador com geolocalizador",
  "type": "flying",
  "attack": 45,
  "heigth": 0.3,
  "defese": 40
}
{
  "_id": ObjectId("56b97c8a4f203473d0d38d43"),
  "name": "Rattata",
  "description": "Pokemon comedor de queijo",
  "type": "normal",
  "attack": 56,
  "heigth": 0.3,
  "defese": 35
}
{
  "_id": ObjectId("56b97c914f203473d0d38d44"),
  "name": "Spearow",
  "description": "Spearow tem um grito muito alto que pode ser ouvido mais de meia milha de distância",
  "type": "flying",
  "attack": 60,
  "heigth": 0.3,
  "defese": 30
}
{
  "_id": ObjectId("56b97c974f203473d0d38d45"),
  "name": "Ekans",
  "description": "Ekans enrola-se em uma espiral enquanto descansa",
  "type": "snake",
  "attack": 60,
  "heigth": 2,
  "defese": 44
}
{
  "_id": ObjectId("56b97c9d4f203473d0d38d46"),
  "name": "vulpix",
  "description": "Na época de seu nascimento, Vulpix tem uma cauda branca.",
  "type": "fire",
  "attack": 40,
  "heigth": 0.6,
  "defese": 41
}
{
  "_id": ObjectId("56b97ca54f203473d0d38d47"),
  "name": "Venonat",
  "description": "Venonat é dito ter evoluído com um casaco de cabelo fino",
  "type": "poison",
  "attack": 55,
  "heigth": 1,
  "defese": 50
}
{
  "_id": ObjectId("56b97cac4f203473d0d38d48"),
  "name": "Meowth",
  "description": "este Pokémon ama moedas brilhantes que brilham com a luz.",
  "type": "normal",
  "attack": 45,
  "heigth": 0.4,
  "defese": 35
}
{
  "_id": ObjectId("56b97cb44f203473d0d38d49"),
  "name": "Mankey",
  "description": " é impossível para qualquer um de fugir a sua ira.",
  "type": "figthing",
  "attack": 80,
  "heigth": 0.5,
  "defese": 40
}
```

## Buscando pokemon, editando e salvando
```
Tto(mongod-3.2.1) be-mean-instagram> var query = {name: 'Mankey'}
Tto(mongod-3.2.1) be-mean-instagram> var pokemon = db.pokemons.findOne(query)
Tto(mongod-3.2.1) be-mean-instagram> pokemon.description = "Esse pokemon foi editado para sevir o exercicio";
Esse pokemon foi editado para sevir o exercicio
Tto(mongod-3.2.1) be-mean-instagram> pokemon
{
  "_id": ObjectId("56b97cb44f203473d0d38d49"),
  "name": "Mankey",
  "description": "Esse pokemon foi editado para sevir o exercicio",
  "type": "figthing",
  "attack": 80,
  "heigth": 0.5,
  "defese": 40
}
Tto(mongod-3.2.1) be-mean-instagram> db.pokemons.save(pokemon)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```


###Correção
Exportando pokemons
```
mongoexport --db be-mean-instagram --collection pokemons --type=json --out=pokemons.json
2016-02-09T04:03:56.394-0200	connected to: localhost
2016-02-09T04:03:56.396-0200	exported 14 records
```
Importado pokemons
```
 mongoexport --db be-mean-instagram --collection pokemons --type=json --out=pokemons.json
2016-02-09T04:03:56.394-0200	connected to: localhost
2016-02-09T04:03:56.396-0200	exported 14 records
Tto(mongod-3.2.1) be-mean-pokemons> show collections
pokemons → 0.002MB / 0.016MB
```

