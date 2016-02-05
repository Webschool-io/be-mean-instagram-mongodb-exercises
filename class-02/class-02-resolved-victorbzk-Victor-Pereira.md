# MongoDB - Aula 02 - Exercício
autor: Victor Pereira

## Listagem das databases (passo 2)

```
victorbzk(mongod-3.0.7) be-mean-pokemons> show dbs 

be-mean-instagram → 0.078GB
be-mean           → 0.078GB 
local             → 0.078GB
```

## Listagem das coleções (passo 3)

```
victorbzk(mongod-3.0.7) be-mean-pokemons> show collections
```

## Cadastro dos pokemons (passo 4)

```
victorbzk(mongod-3.0.7) be-mean-pokemons> var pokemons = [
{name: "Pikachu", description: "Rato elétrico", attack: 50, defense: 30, height:0.5} , {name: "Charmander", description: "Mini-Charizard", attack:40, defense: 20, height:0.6} , {name: "Squirtle", description: "Pokémon astro do pornô", attack:60, defense: 30, height:0.5} , {name: "Bulbassauro", description: "Pokémon da floresta", attack:45, defense: 40, height:0.7} , {name: "Caterpie", description: "Pokémon ET", attack:55, defense: 30, height:0.5} ]

victorbzk(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
```

## Lista dos pokemons (passo 5)

```
victorbzk(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()

{
  "_id": ObjectId("5647b5319dd42619b4f09b74"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 50,
  "defense": 30,
  "height": 0.5
}

{
  "_id": ObjectId("5647b5669dd42619b4f09b75"),
  "name": "Charmander",
  "description": "Mini-Charizard",
  "attack": 40,
  "defense": 20,
  "height": 0.6
}

{
  "_id": ObjectId("5647b5899dd42619b4f09b76"),
  "name": "Squirtle",
  "description": "Pokémon astro do pornô",
  "attack": 60,
  "defense": 30,
  "height": 0.5
}

{
  "_id": ObjectId("5647b5b59dd42619b4f09b77"), 
  "name": "Bulbassauro",
  "description": "Pokémon da floresta",
  "attack": 45,
  "defense": 40
  "height": 0.7
}


{
  "_id": ObjectId("5647b63a9dd42619b4f09b78"),
  "name": "Caterpie",
  "description": "Pokémon ET",
  "attack": 55,
  "defense": 30,
  "height": 0.5
}

Fetched 5 record(s) in 13ms
```

## Pikachu (passo 6)

```
victorbzk(mongod-3.0.7) be-mean-pokemons> var query = {name: "Pikachu"}
victorbzk(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
victorbzk(mongod-3.0.7) be-mean-pokemons> poke

{
  "_id": ObjectId("5647b5319dd42619b4f09b74"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 50,
  "defense": 30,
  "height": 0.5
}
```

## Atualização do Pikachu (passo 6)

```
victorbzk(mongod-3.0.7) be-mean-pokemons> poke.description = "Rato elétrico fofinho demais da conta"
Rato elétrico fofinho demais da conta
victorbzk(mongod-3.0.7) be-mean-pokemons> poke

{
  "_id": ObjectId("5647b5319dd42619b4f09b74"),
  "name": "Pikachu",
  "description": "Rato elétrico fofinho demais da conta",
  "attack": 50,
  "defense": 30,
  "height": 0.5
}

victorbzk(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)

Updated 1 existing record(s) in 9ms

WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```