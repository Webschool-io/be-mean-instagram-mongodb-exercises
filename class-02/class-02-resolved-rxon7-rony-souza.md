# MongoDB - Aula 02 - Exercício
Author: Rony Souza

## Listando as Databases (passo 2)
```
show dbs
```

## Listando Collections
```
show collections(passo 3)
```

## Cadastrando Pokemons(passo 4)
```
var pokemons = [
	
	{name: "Sandshrew", description: "Ground", attack: 40, defense: 40, heigth: 0.6},
	{'name':'Weedle','description':'Minhoca arregaça cú','type':'bug', attack: 30, defense: 10, height: 0.3},
	{name: "Raichu", description: "Eletric", attack: 50, defense: 30, heigth: 0.8}, 
	{'name':'Rapidash','description':'Ta pegando fogo bixo!','type':'fire', attack: 80, defense: 30, height: 1.7},
	{name: "Arceus", description: "Normal", attack: 60, defense: 50, heigth: 3.20} 
]
```
```

db.pokemons.insert(pokemons)
```

## Listagem dos Pokemons
``` 
db.pokemons.find()
```

## Procurando Pokemon Arceus
``` 
var poke = db.pokemons.findOne({name: "Arceus"})
```

## Atualização da propiedade para Fight
``` 
poke.description = "Fight"
db.pokemons.save(poke)
```

