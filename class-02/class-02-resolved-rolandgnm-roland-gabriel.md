
# MongoDB - Aula 02 - Exercício
autor: Roland Gabriel

## Listagem das databases (passo 2)
    be-mean-instagram → 0.078GB
    be-mean-pokemons  → 0.078GB
    be-mean           → 0.078GB
    local             → 0.078GB

## Listagem das coleções (passo 3)
    pokemons       → 0.000MB / 0.008MB
    system.indexes → 0.000MB / 0.008MB


## Cadastro dos pokemons (passo 4)
    #1 db.pokemons.save({ 'name':'Weedle', 'description':'Weedle has an extremely acute sense of smell.', attack: 20, defense: 20, height: 0.3 })
    #2 db.pokemons.save({ 'name':'Kakuna', 'description':'Kakuna remains virtually immobile as it clings to a tree', attack: 10, defense: 20, height: 0.6 })
    #3 db.pokemons.save({ 'name':'Weepinbell', 'description':'Weepinbell has a large hook on its rear end.', attack: 5, defense: 20, height: 1.0 })
    #4 db.pokemons.save({ 'name':'Tentacool', 'description':'Tentacool\'s body is largely composed of water.', attack: 20, defense: 20, height: 0.9 })
    #5 db.pokemons.save({ 'name':'Golem', 'description':'Golem live up on mountains.', attack: 60, defense: 60, height: 1.4 })


## Lista dos pokemons (passo 5)
```
   {
      "_id": ObjectId("56480b9de7df842a0d3aaaf7"),
      "name": "Weedle",
      "description": "Weedle has an extremely acute sense of smell.",
      "attack": 20,
      "defense": 20,
      "height": 0.3
    }
    {
      "_id": ObjectId("56480cc6e7df842a0d3aaaf8"),
      "name": "Kakuna",
      "description": "Kakuna remains virtually immobile as it clings to a tree",
      "attack": 10,
      "defense": 20,
      "height": 0.6
    }
    {
      "_id": ObjectId("56480d32e7df842a0d3aaaf9"),
      "name": "Weepinbell",
      "description": "Weepinbell has a large hook on its rear end.",
      "attack": 5,
      "defense": 20,
      "height": 1
    }
    {
      "_id": ObjectId("56480d9be7df842a0d3aaafa"),
      "name": "Tentacool",
      "description": "Tentacool's body is largely composed of water.",
      "attack": 20,
      "defense": 20,
      "height": 0.9
    }
    {
      "_id": ObjectId("56480e30e7df842a0d3aaafb"),
      "name": "Golem",
      "description": "Golem live up on mountains.",
      "attack": 60,
      "defense": 60,
      "height": 1.4
    }
```

## Tentacool (passo 6)
```
$be-mean-pokemons> poke = db.pokemons.findOne({name: 'Tentacool'})
{
  "_id": ObjectId("56480d9be7df842a0d3aaafa"),
  "name": "Tentacool",
  "description": "Tentacool's body is largely composed of water.",
  "attack": 20,
  "defense": 20,
  "height": 0.9
}
```



## Atualização do Pikachu (passo 6)
```
$be-mean-pokemons> poke.description = 'O corpo do Tentacool é largamente composto por água.'
O corpo do Tentacool é largamente composto por água.

$be-mean-pokemons> poke
{
  "_id": ObjectId("56480d9be7df842a0d3aaafa"),
  "name": "Tentacool",
  "description": "O corpo do Tentacool é largamente composto por água.",
  "attack": 20,
  "defense": 20,
  "height": 0.9
}

$be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
