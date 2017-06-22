# MongoDB - Aula 03 - Exercício
autor: Douglas Salin Zuqueto

## 1.Liste todos os Pokemons com a altura MENOR QUE 0.5

```
fedora(mongod-3.0.4) be-mean-pokemons> var query = {height: {$lt:"0.5"}}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Modificando a Descrição do Pikachu",
  "attack": "30",
  "defense": "20",
  "height": "0.4"
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e4"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison.",
  "attack": "30",
  "defense": "20",
  "height": "0.4"
}
Fetched 2 record(s) in 0ms

```

## 2.Liste todos Pokemons com a altura MAIOR OU IGUAL QUE 0.5

```
fedora(mongod-3.0.4) be-mean-pokemons> var query = {height: {$gte:"0.5"}}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e3"),
  "name": "Sandslash",
  "description": "Sandslash's body is covered by tough spikes, which are hardened sections of its hide.",
  "attack": "50",
  "defense": "50",
  "height": "1.0"
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e5"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "attack": "50",
  "defense": "30",
  "height": "0.8"
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e6"),
  "name": "Sandshrew",
  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert.",
  "attack": "40",
  "defense": "40",
  "height": "0.6"
}
Fetched 3 record(s) in 1ms

```

## 3.Liste todos Pokemons com a altura MENOR OU IGUAL QUE 0.5 E to tipo grama

```
fedora(mongod-3.0.4) be-mean-pokemons> var height = {height: {$lte: "0.5"}}
fedora(mongod-3.0.4) be-mean-pokemons> var type = {type:/grama/}
fedora(mongod-3.0.4) be-mean-pokemons> var query = {$and: [height,type]}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
fedora(mongod-3.0.4) be-mean-pokemons>

```

## 4.Liste todos Pokemons com o name 'Pikachu' OU com attack MENOR OU IGUAL QUE 0.5

```
fedora(mongod-3.0.4) be-mean-pokemons> var name = {name: /pikachu/i}
fedora(mongod-3.0.4) be-mean-pokemons> var attack = {attack:{$lte:"0.5"}}
fedora(mongod-3.0.4) be-mean-pokemons> var query = {$or:[name,attack]}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Modificando a Descrição do Pikachu",
  "attack": "30",
  "defense": "20",
  "height": "0.4"
}
Fetched 1 record(s) in 1ms
fedora(mongod-3.0.4) be-mean-pokemons>

```

## 5.Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height MENOR OU IGUAL QUE 0.5

```
fedora(mongod-3.0.4) be-mean-pokemons> var attack = {attack:{$gte:"48"}}
fedora(mongod-3.0.4) be-mean-pokemons> var height = {height:{$lte:"0.5"}}
fedora(mongod-3.0.4) be-mean-pokemons> var query = {$and:[attack,height]}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```
