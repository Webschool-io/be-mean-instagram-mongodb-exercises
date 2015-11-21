# MongoDB - Aula 02 - Exercício
Author: Rony Souza

## Listando as Databases (passo 2)
```
show dbs

rxon7-desktop(mongod-2.4.14) be-mean-teste> show dbs
be-mean           → 0.203GB
be-mean-teste     → 0.203GB
test              → 0.203GB
local             → 0.078GB

```

## Listando Collections
```
show collections(passo 3)

rxon7-desktop(mongod-2.4.14) be-mean-pokemons> show collections
system.indexes → 0.000MB / 0.008MB


```

## Cadastrando Pokemons(passo 4)
```
var pokemons = [
	
	{name: "Sandshrew", description: "Tatu boladao", attack: 40, defense: 40, heigth: 0.6},
	{'name':'Weedle','description':'Minhoca louca','type':'bug', attack: 30, defense: 10, height: 0.3},
	{name: "Raichu", description: "Eletrico", attack: 50, defense: 30, heigth: 0.8}, 
	{'name':'Rapidash','description':'On fire!','type':'fire', attack: 80, defense: 30, height: 1.7},
	{name: "Arceus", description: "Mitico", attack: 60, defense: 50, heigth: 3.20} 
]

rxon7-desktop(mongod-2.4.14) be-mean-pokemons> pokemons
[
  {
    "name": "Sandshrew",
    "description": "Tatu boladao",
    "attack": 40,
    "defense": 40,
    "heigth": 0.6
  },
  {
    "name": "Weedle",
    "description": "Minhoca louca",
    "type": "bug",
    "attack": 30,
    "defense": 10,
    "height": 0.3
  },
  {
    "name": "Raichu",
    "description": "Eletrico",
    "attack": 50,
    "defense": 30,
    "heigth": 0.8
  },
  {
    "name": "Rapidash",
    "description": "On fire!",
    "type": "fire",
    "attack": 80,
    "defense": 30,
    "height": 1.7
  },
  {
    "name": "Arceus",
    "description": "Mitico",
    "attack": 60,
    "defense": 50,
    "heigth": 3.2
  }


```
```

db.pokemons.insert(pokemons)
```

## Listagem dos Pokemons
``` 
db.pokemons.find()

butu-desktop(mongod-2.4.14) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5650de483a708d4d1c44e60e"),
  "name": "Sandshrew",
  "description": "Ground",
  "attack": 40,
  "defense": 40,
  "heigth": 0.6
}
{
  "_id": ObjectId("5650de483a708d4d1c44e60f"),
  "name": "Weedle",
  "description": "Minhoca arregaça cú",
  "type": "bug",
  "attack": 30,
  "defense": 10,
  "height": 0.3
}
{
  "_id": ObjectId("5650de483a708d4d1c44e610"),
  "name": "Raichu",
  "description": "Eletric",
  "attack": 50,
  "defense": 30,
  "heigth": 0.8
}
{
  "_id": ObjectId("5650de483a708d4d1c44e611"),
  "name": "Rapidash",
  "description": "Ta pegando fogo bixo!",
  "type": "fire",
  "attack": 80,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("5650de483a708d4d1c44e612"),
  "name": "Arceus",
  "description": "Normal",
  "attack": 60,
  "defense": 50,
  "heigth": 3.2
}
{
  "_id": ObjectId("5650f7fc3d5c08c087e86f0e"),
  "name": "Sandshrew",
  "description": "Tatu boladao",
  "attack": 40,
  "defense": 40,
  "heigth": 0.6
}
{
  "_id": ObjectId("5650f7fc3d5c08c087e86f0f"),
  "name": "Weedle",
  "description": "Minhoca louca",
  "type": "bug",
  "attack": 30,
  "defense": 10,
  "height": 0.3
}
{
  "_id": ObjectId("5650f7fc3d5c08c087e86f10"),
  "name": "Raichu",
  "description": "Eletrico",
  "attack": 50,
  "defense": 30,
  "heigth": 0.8
}
{
  "_id": ObjectId("5650f7fc3d5c08c087e86f11"),
  "name": "Rapidash",
  "description": "On fire!",
  "type": "fire",
  "attack": 80,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("5650f7fc3d5c08c087e86f12"),
  "name": "Arceus",
  "description": "Mitico",
  "attack": 60,
  "defense": 50,
  "heigth": 3.2
}

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

