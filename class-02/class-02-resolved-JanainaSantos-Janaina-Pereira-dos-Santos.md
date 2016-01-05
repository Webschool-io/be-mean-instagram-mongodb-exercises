# MongoDB - Aula 02 - Exercício
autor: Janaína P. dos Santos

## 1. Criar uma database chamada be-mean-pokemons
```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## 2. Listando Databases 
```
show dbs
```

## 3. Listando Collections
```
show collections
```

## 4. Cadastrando Pokemons
```
var pokemon = {name:"Blastoise", description: "Projetar água.", attack: 75, defense: 30, height: 1.6 }
db.pokemons.insert(pokemon)
var pokemon = {name:"Raichu", description: "Eletric", attack: 50, defense: 30, heigth: 0.8}
db.pokemons.insert(pokemon)
var pokemon = {name:"Sandshrew", description:"Ground", attack: 40, defense: 40, heigth: 0.6}
db.pokemons.insert(pokemon)
var pokemon = {name:"Wurmple", description: "Descasca a casca das árvores", attack: 35,  defense: 30, height: 0.3 }
db.pokemons.insert(pokemon)
var pokemon = {name:"Serperior", description: "Grass", attack: 40, defense: 40, heigth: 3.30}
db.pokemons.insert(pokemon) 	
```

## 5. Listagem dos Pokemons
``` 
db.pokemons.find()
```

## 6. Procurando Pokemon Wurmple
### Usando o seletor para poder mudar a propiedade :)
``` 
var pok = db.pokemons.findOne({name: "Wurmple"})
```

## 7. Atualização da propiedade para Fight
``` 
pok.description = "Descascar árvore"
db.pokemons.save(pok)
```

	

 
 


