# MongoDB - Aula 02 - Exercício
autor: Igor Vidotto Felipe

## 1 - Criação da database be-mean-pokemons 
#### Entrada
```igorpc(mongod-3.0.7) be-mean-pokemons> use be-mean-pokemons```

#### Saída
> switched to db be-mean-pokemons


## 2 - Listagem das databases 
#### Entrada
`igorpc(mongod-3.0.7) be-mean-pokemons> show dbs`

#### Saída
>```
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
```


## 3 - Listagem das coleções
#### Entrada
`igorpc(mongod-3.0.7) be-mean-pokemons> show collections`

#### Saída
> não retorna nada, pois ainda não foi inserido nenhum dado nessa db


## 4 - Cadastro dos pokemons

### Primeiro Pokémon
#### Entrada
```
igorpc(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({name: "Jigglypuff", description: "Uma bolinha de pelos rosa que canta", type: "normal/fada", attack: 45, defense: 20, height: 0.5})
```

#### Saída
>```
Inserted 1 record(s) in 392ms
WriteResult({
  "nInserted": 1
})
```

### Segundo Pokémon
#### Entrada
```
igorpc(mongod-3.0.7) be-mean-pokemons> var pokemon = {name: "Ninetales", description: "Cachorro/Lobo que possui nove caldas (ah vá)", type: "fogo", attack: 76, defense: 75, height: 1.1}

```
`igorpc(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)`

#### Saída
>```
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

### Três últimos Pokémons
#### Entrada
```
igorpc(mongod-3.0.7) be-mean-pokemons> var arrayPokemons = [
	{name: "Charizard", description: "Dragão fodelão motherfucker que AshNoob abandona", type: "fogo/voador", attack: 84, defense: 78, height: 1.7 },
	{name: "ButterFree", description: "Última evolução do Caterpie, nesse estágio se torna uma borboleta (Ash também abandona)", type: "inseto/voador", attack: 45, defense: 50, height: 1.1},
	{name: "Pidgeot", description: "Pássaro muito grande, um dos pokémons normais/voadores mais fortes", type: "normal/voador", attack: 80, defense: 75, height: 1.5}
]
```

`igorpc(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(arrayPokemons)`

#### Saída
>```
Inserted 1 record(s) in 1ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 3,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```




## 5 - Lista dos pokemons
#### Entrada
`igorpc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()`

#### Saída
>```
{
  "_id": ObjectId("5648ddb64ad4e0bc95c83704"),
  "name": "Jigglypuff",
  "description": "Uma bolinha de pelos rosa que canta",
  "type": "normal/fada",
  "attack": 45,
  "defense": 20,
  "height": 0.5
}
{
  "_id": ObjectId("5648df814ad4e0bc95c83705"),
  "name": "Ninetales",
  "description": "Cachorro/Lobo que possui nove caldas (ah vá)",
  "type": "fogo",
  "attack": 76,
  "defense": 75,
  "height": 1.1
}
{
  "_id": ObjectId("5648e67e4ad4e0bc95c83706"),
  "name": "Charizard",
  "description": "Dragão fodelão motherfucker que AshNoob abandona",
  "type": "fogo/voador",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("5648e67e4ad4e0bc95c83707"),
  "name": "ButterFree",
  "description": "Última evolução do Caterpie, nesse estágio se torna uma borboleta (Ash também abandona)",
  "type": "inseto/voador",
  "attack": 45,
  "defense": 50,
  "height": 1.1
}
{
  "_id": ObjectId("5648e67e4ad4e0bc95c83708"),
  "name": "Pidgeot",
  "description": "Pássaro muito grande, um dos pokémons normais/voadores mais fortes",
  "type": "normal/voador",
  "attack": 80,
  "defense": 75,
  "height": 1.5
}
Fetched 5 record(s) in 4ms
```



## 6 - Pokémon
#### Entrada
```
igorpc(mongod-3.0.7) be-mean-pokemons> var query = {name: "Pidgeot"}
igorpc(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
igorpc(mongod-3.0.7) be-mean-pokemons> poke
```

#### Saída
>```
{
  "_id": ObjectId("5648e67e4ad4e0bc95c83708"),
  "name": "Pidgeot",
  "description": "Pássaro muito grande, um dos pokémons normais/voadores mais fortes",
  "type": "normal/voador",
  "attack": 80,
  "defense": 75,
  "height": 1.5
}
```

## 7 - Atualização do Pokémon
### Alterando a variável poke 
#### Entrada
```
igorpc(mongod-3.0.7) be-mean-pokemons> poke.description = "Pássaro muito grande, um dos pokémons normais/voadores mais fortes (Ah esqueci, Ash vacilão também abandonou -.-)"
```
```
igorpc(mongod-3.0.7) be-mean-pokemons> poke
```

#### Saída
>```
{
  "_id": ObjectId("5648e67e4ad4e0bc95c83708"),
  "name": "Pidgeot",
  "description": "Pássaro muito grande, um dos pokémons normais/voadores mais fortes (Ah esqueci, Ash vacilão também abandonou -.-)",
  "type": "normal/voador",
  "attack": 80,
  "defense": 75,
  "height": 1.5
}
```

### Salvando a alteração na db
#### Entrada
```
igorpc(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
```

#### Saída
>```
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

