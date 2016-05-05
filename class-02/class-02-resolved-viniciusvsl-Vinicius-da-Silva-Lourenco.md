# MongoDB - Aula 02 - Exercício
autor: Vinicius da Silva Lourenço

## Criação da databases (passo 1)
```
use be-mean-pokemon
switched to db be-mean-pokemon
```

## Listagem das databases (passo 2)
```
show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
local             → 0.000GB
```

## Listagem das coleções (passo 3)
```
show collections
```

## Cadastro dos pokemons (passo 4)
```
var pokemon={name:'Charizard', description:'Dragão irado', type:'Fire', attack:84, defense:78, height:17}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 176ms
WriteResult({
  "nInserted": 1
})

var pokemon={name:'Rhydon', description:'Pokemon furadeira', type:'Rock', attack:130, defense:120, height:19}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

var pokemon={name:'Scyther', description:'Pokemon pata de navalha', type:'Bug', attack:110, defense:80, height:15}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

var pokemon={name:'Tauros', description:'É casado com uma vaca', type:'Normal', attack:100, defense:95, height:14}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

var pokemon={name:'Growlithe', description:'O melhor amigo do treinador', type:'Fire', attack:70, defense:45, height:7}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

```

## Lista dos pokemons (passo 5)
```
db.pokemons.find()
{
  "_id": ObjectId("56ba84d2e598513a5fdf9df0"),
  "name": "Charizard",
  "description": "Dragão irado",
  "type": "Fire",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("56ba8686b3687ee4ec501c37"),
  "name": "Rhydon",
  "description": "Pokemon furadeira",
  "type": "Rock",
  "attack": 130,
  "defense": 120,
  "height": 19
}
{
  "_id": ObjectId("56ba879059458202531d7e48"),
  "name": "Scyther",
  "description": "Pokemon pata de navalha",
  "type": "Bug",
  "attack": 110,
  "defense": 80,
  "height": 15
}
{
  "_id": ObjectId("56ba885b59458202531d7e49"),
  "name": "Tauros",
  "description": "É casado com uma vaca",
  "type": "Normal",
  "attack": 100,
  "defense": 95,
  "height": 14
}
{
  "_id": ObjectId("56ba88e059458202531d7e4a"),
  "name": "Growlithe",
  "description": "O melhor amigo do treinador",
  "type": "Fire",
  "attack": 70,
  "defense": 45,
  "height": 7
}
Fetched 5 record(s) in 5ms
```

## Pokemon (passo 6)
```
var query={name:'Charizard'}
var poke=db.pokemons.findOne(query)
poke
{
  "_id": ObjectId("56ba84d2e598513a5fdf9df0"),
  "name": "Charizard",
  "description": "Dragão irado",
  "type": "Fire",
  "attack": 84,
  "defense": 78,
  "height": 17
}
```

## Atualização do Pokemon (passo 7)
```
poke.description='Um dragão poderoso e orgulhoso'
Um dragão poderoso e orgulhoso

db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
