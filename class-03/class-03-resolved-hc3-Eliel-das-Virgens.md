


# Liste todos os pokemons com altura menor que 0.5
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {height:{$lt:0.5}}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {height:{$lt:1.2}}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b74890b4620a5d4ec2cb53"),
  "name": "Bnegao",
  "description": "Pokemon pensador",
  "attack": "150",
  "defense": "400",
  "height": 1.1
}
{
  "_id": ObjectId("56b74894b4620a5d4ec2cb54"),
  "name": "Marcelo D2",
  "description": "Pokemon Smoke Hard",
  "attack": "350",
  "defense": "500",
  "height": 1
}
Fetched 2 record(s) in 0ms
```

#Liste todos os pokemons com altura maior ou igual que 0.5
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {height:{$gte:0.5}}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b7478eb4620a5d4ec2cb52"),
  "name": "Black Alien Mon",
  "description": "Pokemon da Rima",
  "attack": "250",
  "defense": "300",
  "height": 1.3
}
{
  "_id": ObjectId("56b74890b4620a5d4ec2cb53"),
  "name": "Bnegao",
  "description": "Pokemon pensador",
  "attack": "150",
  "defense": "400",
  "height": 1.1
}
{
  "_id": ObjectId("56b74894b4620a5d4ec2cb54"),
  "name": "Marcelo D2",
  "description": "Pokemon Smoke Hard",
  "attack": "350",
  "defense": "500",
  "height": 1
}
{
  "_id": ObjectId("56b74897b4620a5d4ec2cb55"),
  "name": "Formiga",
  "description": "Pokemon do Baixo",
  "attack": "50",
  "defense": "200",
  "height": 1.4
}
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2
}
{
  "_id": ObjectId("56b7489bb4620a5d4ec2cb57"),
  "name": "Speed Freaks",
  "description": "Pokemon Flow ou Levada",
  "attack": "500",
  "defense": 900,
  "height": 1.2
}
Fetched 6 record(s) in 1ms
```

#Liste todos os pokemons com altura menor ou igual que 0.5 E do tipo grama
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {$or: [{height:{$lte:0.5}} , {type:'grass'}]}
darkSide(mongod-2.6.3) be-mean-pokemons> query
{
  "$or": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grass"
    }
  ]
}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {$or: [{height:{$lte:1.2}} , {type:'grass'}]}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b74890b4620a5d4ec2cb53"),
  "name": "Bnegao",
  "description": "Pokemon pensador",
  "attack": "150",
  "defense": "400",
  "height": 1.1
}
{
  "_id": ObjectId("56b74894b4620a5d4ec2cb54"),
  "name": "Marcelo D2",
  "description": "Pokemon Smoke Hard",
  "attack": "350",
  "defense": "500",
  "height": 1
}
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2
}
{
  "_id": ObjectId("56b7489bb4620a5d4ec2cb57"),
  "name": "Speed Freaks",
  "attack": "500",
  "description": "Pokemon Flow ou Levada",
  "defense": 900,
  "height": 1.2
}
Fetched 4 record(s) in 4ms

```

#Liste todos os pokemons com name 'pikachu' ou com attack menor ou igual que 0.5
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {$or: [{name:'Pikachu'} , {attack:{$lte:0.5}}]}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {$or: [{name:'Pedrinho'} , {attack:{$lte:0.5}}]}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2
}
Fetched 1 record(s) in 1ms

```

#Liste todos os pokemons com attack maior ou igual que 48 e com height menor ou igual que 0.5
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {$and [ {attack:{$gte:48}} , {height: {$lte:0.5}} ]}
2016-02-07T18:51:25.863-0300 SyntaxError: Unexpected token [
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {$and: [ {attack:{$gte:48}} , {height: {$lte:0.5}} ]}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b7bbf7b4620a5d4ec2cb5b"),
  "name": "pikachu",
  "description": "poderes eletricos",
  "attack": 48,
  "defense": 100,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```
