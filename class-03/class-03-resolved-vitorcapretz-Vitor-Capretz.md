# MongoDB - Aula 03 - Exercício
autor: Vitor Capretz


# Liste todos Pokemons com a altura menor que 0.5
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find({height: {$lt: 0.5}})
{
  "_id": ObjectId("57476d07361178273f8391d8"),
  "name": "Bulbassauro",
  "description": "aquele verde",
  "type": "Grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57476d07361178273f8391db"),
  "name": "Pikachu",
  "description": "pokemon de poser",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
{
  "_id": ObjectId("574779c0361178273f8391dd"),
  "name": "Pidgey",
  "description": "rolinha que nao voa",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "type": "Voador"
}
Fetched 3 record(s) in 1ms


```
# Liste todos Pokemons com a altura maior ou igual que 0.5
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find({height: {$gte: 0.5}})
{
  "_id": ObjectId("57476d07361178273f8391d9"),
  "name": "Charmander",
  "description": "o que vira o charizard (fodelao)",
  "type": "Fogo",
  "attack": 52,
  "defense": 43,
  "height": 0.6
}
{
  "_id": ObjectId("57476d07361178273f8391da"),
  "name": "Squirtle",
  "description": "esse evoluido tbm eh massa",
  "type": "Água",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
{
  "_id": ObjectId("57476d07361178273f8391dc"),
  "name": "Jigglypuff",
  "description": "prof da aula de historia",
  "type": "Fada",
  "attack": 45,
  "defense": 40,
  "height": 0.51
}
Fetched 3 record(s) in 1ms


```
# Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find({$and: [{height: {$lte: 0.5}}, {type: "Grama"}]})
{
  "_id": ObjectId("57476d07361178273f8391d8"),
  "name": "Bulbassauro",
  "description": "aquele verde",
  "type": "Grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms


```
# Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find({$or: [{attack: {$lte: 0.5}}, {name: "Pikachu"}]})
{
  "_id": ObjectId("57476d07361178273f8391db"),
  "name": "Pikachu",
  "description": "pokemon de poser",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
Fetched 1 record(s) in 1ms


```
# Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find({$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]})
{
  "_id": ObjectId("57476d07361178273f8391d8"),
  "name": "Bulbassauro",
  "description": "aquele verde",
  "type": "Grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57476d07361178273f8391da"),
  "name": "Squirtle",
  "description": "esse evoluido tbm eh massa",
  "type": "Água",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
{
  "_id": ObjectId("57476d07361178273f8391db"),
  "name": "Pikachu",
  "description": "pokemon de poser",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
Fetched 3 record(s) in 2ms

```
