# MongoDB - Aula 02 - Exercício
User: https://github.com/jacksonfraga
Autor: Jackson de Fraga

## Criar uma database
```
use be-mean-pokemons
```

## Listar databases
```
show dbs
```

## Listar coleções na base atual
```
show collections
```

## Inserir 5 pokemons
```
var pokemon = { name : 'Pikachu', description: 'Rato elétrico bem fofinho', type: 'eletric', attack: 55, defense: 35, height: 0.4 }
db.pokemons.insert(pokemon)

pokemon = { name : 'Charmander', description: 'Lizard Pokémon', type: 'fire', attack: 52, defense: 43, height: 0.6 }
db.pokemons.insert(pokemon)

pokemon = { name : 'Blastoise', description: 'Shellfish Pokémon', type: 'Water', attack: 83, defense: 100, height: 1.6 }
db.pokemons.insert(pokemon)

pokemon = { name : 'Mankey', description: 'Pig Monkey Pokémon', type: 'Fighting', attack: 80, defense: 35, height: 0.5 }
db.pokemons.insert(pokemon)

pokemon = { name : 'Kadabra', description: 'Psi Pokémon', type: 'Psychic', attack: 35, defense: 30, height: 1.3 }
db.pokemons.insert(pokemon)

pokemon = { name : 'Pinsir', description: 'Stag Beetle Pokémon', type: 'Bug', attack: 125, defense: 100, height: 1.5 }
db.pokemons.insert(pokemon)
```

## Listar pokemons existentes
```
db.pokemons.find({})
```

## Buscar pokemon e armazenar na variavel
```
var query = { name : 'Pikachu' }
var poke = db.pokemons.findOne(query)
```

## Modificar e salva
```
poke.description = 'Descrição modificada'
db.pokemons.save(poke);
```