
# MongoDB - Aula 02 - Exercício
autor: Ciro Valente Filho

## Listagem das databases (passo 2)


```
suissacorp(mongod-3.0.6) use be-mean-pokemons
switched to db be-mean-pokemons

localhost(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-pokemons   0.078GB
test               0.078GB
local              0.078GB
be-mean-instagram  0.078GB
```

## Listagem das coleções (passo 3)

```
show collections
localhost(mongod-3.0.7) be-mean-pokemons> 
```

## Cadastro dos pokemons (passo 4)

```
be-mean-pokemons> var pokemon = {'name':'Totodile','description':'jacare Azul','type':'Agua', attack:30, height:0.9}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted"

be-mean-pokemons> var pokemon = {'name':'Mew','description':'pokemon rosa do mal','type':'Psiquico', attack:90, height:0.4}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted"


be-mean-pokemons> var pokemon = {'name':'Jigglypuff ','description':'pokemon chato pacas','type':'Normal', attack:20, height:0.5}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted"


be-mean-pokemons> var pokemon = {'name':'Charizard ','description':'pokemon fodao','type':'Fogo', attack:20, height:90}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted"
  
  
be-mean-pokemons> var pokemon = {'name':'Snorlax','description':'Gato Grande','type':'Normal', attack:100, height:1000}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted"
  })
   
```

## Lista dos pokemons (passo 5)


```
be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564a7826d6905d59d846bf0f"),
  "name": "Totodile",
  "description": "jacare Azul",
  "type": "Agua",
  "attack": 30,
  "height": 0.9
}
{
  "_id": ObjectId("564a7844d6905d59d846bf10"),
  "name": "Mew",
  "description": "pokemon rosa do mal",
  "type": "Psiquico",
  "attack": 90,
  "height": 0.4
}
{
  "_id": ObjectId("564a7877d6905d59d846bf11"),
  "name": "Charizard ",
  "description": "pokemon fodao",
  "type": "Fogo",
  "attack": 20,
  "height": 90
}
{
  "_id": ObjectId("564a787cd6905d59d846bf12"),
  "name": "Jigglypuff ",
  "description": "pokemon chato pacas",
  "type": "Normal",
  "attack": 20,
  "height": 0.5
}
{
  "_id": ObjectId("564a79603931d0f16891c3dc"),
  "name": "Snorlax",
  "description": "Gato Grande",
  "type": "Normal",
  "attack": 100,
  "height": 1000
}

Fetched 5 record(s) in 3ms


```

## Pokemon (passo 6)

```
var query = {type: 'Fogo'}

be-mean-pokemons> var poke = db.pokemons.findOne(query)

be-mean-pokemons> poke
{
  "_id": ObjectId("564a7877d6905d59d846bf11"),
  "name": "Charizard ",
  "description": "pokemon fodao",
  "type": "Fogo",
  "attack": 20,
  "height": 90
}

```

## Atualização do Pokemon (passo 7)

```
 be-mean-pokemons> poke.description = 'Pokemon é foão mano'
Pokemon é foão mano

be-mean-pokemons> poke
{
  "_id": ObjectId("564a7877d6905d59d846bf11"),
  "name": "Charizard ",
  "description": "Pokemon é foão mano",
  "type": "Fogo",
  "attack": 20,
  "height": 90
}


```

