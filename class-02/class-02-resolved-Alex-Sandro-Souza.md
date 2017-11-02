
# MongoDB - Aula 02 - Exercício
autor: Alex Sandro Souza

## Cria a database (passo 1)

```
gigantus(mongod-3.2.17) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons

```

## Lista as databases (passo 2)

```
gigantus(mongod-3.2.17) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
local             → 0.000GB

```

## Listagem das coleções (passo 3)

```
gigantus(mongod-3.2.17) be-mean-pokemons> show collections

```

## Cadastro dos pokemons (passo 4)

```
gigantus(mongod-3.2.17) be-mean-pokemons> var pokemon = {'name':'Venusaur','description':'Há uma grande flor nas costas de Venusaur','type':'grama',attack:40,height:2.0}
gigantus(mongod-3.2.17) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 27ms
WriteResult({
"nInserted": 1
})
gigantus(mongod-3.2.17) be-mean-pokemons> var pokemon = {'name':'Charizard','description':'Charizard voa ao redor do céu em busca de adversários poderosos','type':'fogo',attack:41,height:1.7}
gigantus(mongod-3.2.17) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
"nInserted": 1
})
gigantus(mongod-3.2.17) be-mean-pokemons> var pokemon = {'name':'Wartortle','description':'Sua cauda é grande e coberta com uma pele rica e grossa','type':'agua',attack:35,height:1.0}
gigantus(mongod-3.2.17) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
"nInserted": 1
})
gigantus(mongod-3.2.17) be-mean-pokemons> var pokemon = {'name':'Butterfree','description':'Borboleta que gosta de mel','type':'inseto',attack:20,height:1.1}
gigantus(mongod-3.2.17) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
"nInserted": 1
})
gigantus(mongod-3.2.17) be-mean-pokemons> var pokemon = {'name':'Articuno','description':'Articuno é um Pokémon de pássaro lendário que pode controlar o gelo','type':'gelo',attack:40,height:1.7}
gigantus(mongod-3.2.17) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
"nInserted": 1
})

```

## Lista dos pokemons (passo 5)

```
gigantus(mongod-3.2.17) be-mean-pokemons> db.pokemons.find()
{
"_id": ObjectId("59f912e2c001c8fb0e0b7d33"),
"name": "Venusaur",
"description": "Há uma grande flor nas costas de Venusaur",
"type": "grama",
"attack": 40,
"height": 2
}
{
"_id": ObjectId("59f91342c001c8fb0e0b7d34"),
"name": "Charizard",
"description": "Charizard voa ao redor do céu em busca de adversários poderosos",
"type": "fogo",
"attack": 41,
"height": 1.7
}
{
"_id": ObjectId("59f913efc001c8fb0e0b7d35"),
"name": "Wartortle",
"description": "Sua cauda é grande e coberta com uma pele rica e grossa",
"type": "agua",
"attack": 35,
"height": 1
}
{
"_id": ObjectId("59f9146ac001c8fb0e0b7d36"),
"name": "Butterfree",
"description": "Borboleta que gosta de mel",
"type": "inseto",
"attack": 20,
"height": 1.1
}
{
"_id": ObjectId("59f914c8c001c8fb0e0b7d37"),
"name": "Articuno",
"description": "Articuno é um Pokémon de pássaro lendário que pode controlar o gelo",
"type": "gelo",
"attack": 40,
"height": 1.7
}
Fetched 5 record(s) in 5ms
gigantus(mongod-3.2.17) be-mean-pokemons> var busca = db.pokemons.find({name:'Articuno'})
gigantus(mongod-3.2.17) be-mean-pokemons> var poke = db.pokemons.findOne({name:'Articuno'})
gigantus(mongod-3.2.17) be-mean-pokemons> poke
{
"_id": ObjectId("59f914c8c001c8fb0e0b7d37"),
"name": "Articuno",
"description": "Articuno é um Pokémon de pássaro lendário que pode controlar o gelo",
"type": "gelo",
"attack": 40,
"height": 1.7
}
Fetched 5 record(s) in 5ms

```


## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

```
gigantus(mongod-3.2.17) be-mean-pokemons> var busca = {name:'Articuno'}
gigantus(mongod-3.2.17) be-mean-pokemons> var poke = db.pokemons.findOne(busca)
gigantus(mongod-3.2.17) be-mean-pokemons> poke
{
"_id": ObjectId("59f914c8c001c8fb0e0b7d37"),
"name": "Articuno",
"description": "Pokémon de pássaro que pode controlar o gelo",
"type": "gelo",
"attack": 40,
"height": 1.7
}


```

## Atualização do Pikachu (passo 7)

```
gigantus(mongod-3.2.17) be-mean-pokemons> poke.description = 'Pokémon de pássaro que pode controlar o gelo'
Pokémon de pássaro que pode controlar o gelo

gigantus(mongod-3.2.17) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
"nMatched": 1,
"nUpserted": 0,
"nModified": 1
})

```
