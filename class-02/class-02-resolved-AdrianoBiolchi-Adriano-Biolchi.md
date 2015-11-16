# MongoDB - Aula 02 - Exercício
Author: Adriano Biolchi

## Listando Databases 
```
show dbs
```

## Listando Collections
```
show collections
```

## Cadastrando Pokemons
```
var regPokemons = [
	{name: "Raichu", description: "Eletric", attack: 50, defense: 30, heigth: 0.8}, 
	{name: "Sandshrew", description: "Ground", attack: 40, defense: 40, heigth: 0.6},
	{name: "Emboar", description: "Fire, Fighting", attack: 60, defense: 30, heigth: 1.60},
	{name: "Serperior", description: "Grass", attack: 40, defense: 40, heigth: 3.30},
	{name: "Arceus", description: "Normal", attack: 60, defense: 50, heigth: 3.20} 
]
```
```

db.pokemons.insert(regPokemons)
```

## Listagem dos Pokemons
``` 
db.pokemons.find()
```

## Procurando Pokemon Arceus
### Usando o seletor para poder mudar a propiedade :)
``` 
var poke = db.pokemons.findOne({name: "Arceus"})
```

## Atualização da propiedade para Fight
``` 
poke.description = "Fight"
db.pokemons.save(poke)
```
