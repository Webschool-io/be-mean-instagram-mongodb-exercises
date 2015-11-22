# MongoDB - Aula 02 - Exercício
Autor: Rony Souza

## Listando as Databases (passo 2)
```
show dbs

rxon7-desktop(mongod-2.4.14) be-mean-teste> show dbs
be-mean           → 0.203GB
be-mean-teste     → 0.203GB
test              → 0.203GB
local             → 0.078GB

```

## Listando Collections(passo 3)
```
show collections

rxon7-desktop(mongod-2.4.14) be-mean-pokemons> show collections
pokemons       → 0.002MB / 0.008MB
system.indexes → 0.000MB / 0.008MB


```

## Cadastrando Pokemons(passo 4)
```
var pokemons = [

	{name: "Bulbasauro", description: "Tatu boladao", attack: 40, defense: 40, heigth: 0.6},
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
#### Inserindo no BD
```

db.pokemons.insert(pokemons)
```

## Listagem dos Pokemons(passo 5)
``` 
db.pokemons.find()

butu-desktop(mongod-2.4.14) be-mean-pokemons> db.pokemons.find()

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
  "_id": ObjectId("5651b993ee01bb113f2be175"),
  "name": "Bulbasaur",
  "description": "Tatu boladao",
  "attack": 40,
  "defense": 40,
  "heigth": 0.6
}
{
  "_id": ObjectId("5651b993ee01bb113f2be177"),
  "name": "Raichu",
  "description": "Eletrico",
  "attack": 50,
  "defense": 30,
  "heigth": 0.8
}
{
  "_id": ObjectId("5651e832460fd1a91b124342"),
  "name": "Sandshrew",
  "description": "Tatu boladao",
  "attack": 40,
  "defense": 40,
  "heigth": 0.6
}
Fetched 20 record(s) in 5ms -- More[true]

```

## Buscar pokemon e armazenar na variavel poke(passo 6)
``` 
rxon7-desktop(mongod-2.4.14) be-mean-pokemons> var query = {name: "Bulbasauro"}
rxon7-desktop(mongod-2.4.14) be-mean-pokemons> var poke = db.pokemons.findOne(query)
rxon7-desktop(mongod-2.4.14) be-mean-pokemons> poke
{
  "_id": ObjectId("5651e87f460fd1a91b124347"),
  "name": "Bulbasauro",
  "description": "Tatu boladao",
  "attack": 40,
  "defense": 40,
  "heigth": 0.6

}
Fetched 1 record(s) in 27ms



```
## Atualização da propiedade description(passo 7)
``` 
rxon7-desktop(mongod-2.4.14) be-mean-pokemons> poke.description
Tatu boladao

rxon7-desktop(mongod-2.4.14) be-mean-pokemons> poke.description = "Pokemon Hacker/aluno"
Pokemon Hacker/aluno

rxon7-desktop(mongod-2.4.14) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 126ms


rxon7-desktop(mongod-2.4.14) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("5651e87f460fd1a91b124347"),
  "name": "Bulbasauro",
  "description": "Pokemon Hacker/aluno",
  "attack": 40,
  "defense": 40,
  "heigth": 0.6
  
 }

```

