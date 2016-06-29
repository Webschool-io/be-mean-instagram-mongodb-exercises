pokemon# MongoDb - Aula 02 - Exercício
autor: Carlos A A Barreto

## Criando a database
```
carlos@carlos-VirtualBox:~$ mongo
MongoDB shell version: 2.4.9
connecting to: test
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando as databases
```
> show databases
be-mean	0.203125GB
be-mean-instagram	0.203125GB
be-mean-pokemons	(empty)
local	0.078125GB
teste	(empty)
```

## Listando as collections
```
> show collections
```

## Inserindo 5 pokemons na coeleção pokemons
```
> var pokemon1 = {'name': "pikachu", 'description': "Rato de raio", 'attack': 55, 'defense': 40, 'height': 4}
> var pokemon2 = {'name': "charizard", 'description': "Lagarto de asas que cospe fogo", 'attack': 84, 'defense': 78, 'height': 17}
> var pokemon3 = {'name': "blastoise", 'description': "Tartaruga bolada", 'attack': 83, 'defense': 100, 'height': 16}
> var pokemon4 = {'name': "porygon", 'description': "Lego", 'attack': 60, 'defense': 70, 'height': 8}
> var pokemon5 = {'name': "raichu", 'description': "Rato de raio boladão", 'attack': 90, 'defense': 55, 'height': 8}
> db.pokemons.insert(pokemon1)
> db.pokemons.inser(pokemon2)
> db.pokemons.insert(pokemon2)
> db.pokemons.insert(pokemon3)
> db.pokemons.insert(pokemon4)
> db.pokemons.insert(pokemon5)
```

## Listando os pokemons existentes na coleção pokemons
```
> db.pokemons.find()
{ "_id" : ObjectId("564a2da728ccce8415450488"), "name" : "pikachu", "description" : "Rato de raio", "attack" : 55, "defense" : 40, "height" : 4 }
{ "_id" : ObjectId("564a2db728ccce8415450489"), "name" : "charizard", "description" : "Lagarto de asas que cospe fogo", "attack" : 84, "defense" : 78, "height" : 17 }
{ "_id" : ObjectId("564a2dbb28ccce841545048a"), "name" : "blastoise", "description" : "Tartaruga bolada", "attack" : 83, "defense" : 100, "height" : 16 }
{ "_id" : ObjectId("564a2dbd28ccce841545048b"), "name" : "porygon", "description" : "Lego", "attack" : 60, "defense" : 70, "height" : 8 }
{ "_id" : ObjectId("564a2dc028ccce841545048c"), "name" : "raichu", "description" : "Rato de raio boladão", "attack" : 90, "defense" : 55, "height" : 8 }
```

## Busca do pokemon pelo nome
```
> var poke = {'name': "raichu"}
> var p = db.pokemons.findOne(poke)
```

## Modificando a 'description' do pokemon encontrado e salvando na collection a alteração
```
> p.description = 'Ratazana elétrica boladona'
Ratazana elétrica boladona
> db.pokemons.save(p)
> db.pokemons.find()
{ "_id" : ObjectId("564a2da728ccce8415450488"), "name" : "pikachu", "description" : "Rato de raio", "attack" : 55, "defense" : 40, "height" : 4 }
{ "_id" : ObjectId("564a2db728ccce8415450489"), "name" : "charizard", "description" : "Lagarto de asas que cospe fogo", "attack" : 84, "defense" : 78, "height" : 17 }
{ "_id" : ObjectId("564a2dbb28ccce841545048a"), "name" : "blastoise", "description" : "Tartaruga bolada", "attack" : 83, "defense" : 100, "height" : 16 }
{ "_id" : ObjectId("564a2dbd28ccce841545048b"), "name" : "porygon", "description" : "Lego", "attack" : 60, "defense" : 70, "height" : 8 }
{ "_id" : ObjectId("564a2dc028ccce841545048c"), "name" : "raichu", "description" : "Ratazana elétrica boladona", "attack" : 90, "defense" : 55, "height" : 8 }
```
