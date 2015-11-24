# MongoDB - Aula 02 - Exercício
Autor: Thiago Nogueira

## Listagem das databases
```
show databases
```

## Listagem das coleções
```
show collections
```

## Cadastro dos pokemons
``` JavaScript
var pokemonArray = [
	{name: "Bulbasaur", description: "Muito doido", attack: 77, defense: 68, heigth: 0.7},
	{name: "Pikachu", description: "Chupa cuscuz", attack: 32, defense: 50, heigth: 1.59},
	{name: "Spearow", description: "Toma muita cachaça", attack: 70, defense: 66, heigth: 1.0},
	{name: "Metapod", description: "Alta periculosidade", attack: 80, defense: 44, heigth: 0.9},
	{name: "Squirtle", description: "Papangu de orelha", attack: 28, defense: 55, heigth: 0.5}
]
```
```

db.pokemons.insert(pokemonArray)
```

## Lista dos pokemons
``` JavaScript
db.pokemons.find()
```

## Procurando Pokemon

``` JavaScript
var poke = db.pokemons.findOne({name: "Pikachu"})
```

## Atualizar Pokemon
``` JavaScript
poke.description = "Faz porra nenhuma"
db.pokemons.save(poke)
```
