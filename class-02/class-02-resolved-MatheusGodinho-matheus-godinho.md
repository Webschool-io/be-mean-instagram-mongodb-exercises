# MongoDB - Aula 02 - Exercício
Matheus Godinho

## 1. Criar uma database chamada be-mean-pokemons
```
MACBEPIDUCB174(mongod-3.2.1) test> use be-mean-pokemons
switched to db be-mean-pokemons

```

## 2. Listando Databases 
```
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean → 0.004GB
local   → 0.000GB
```

## 3. Listando Collections
```
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> show collections

```

## 4. Cadastrando Pokemons
```
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> var pokemon = {name:"Blastoise", description: "Projetar água.", attack: 75, defense: 30, height: 1.6 }
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 27ms
WriteResult({
  "nInserted": 1
})
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> var pokemon = {name:"Raichu", description: "Eletric", attack: 50, defense: 30, heigth: 0.8}
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> var pokemon = {name:"Sandshrew", description:"Ground", attack: 40, defense: 40, heigth: 0.6}
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> var pokemon = {name:"Wurmple", description: "Descasca a casca das árvores", attack: 35,  defense: 30, height: 0.3 }
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> var pokemon = {name:"Serperior", description: "Grass", attack: 40, defense: 40, heigth: 3.30}
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon) 
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

```

## 5. Listagem dos Pokemons
``` 
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56b79abb2464ce3e718b254c"),
  "name": "Blastoise",
  "description": "Projetar água.",
  "attack": 75,
  "defense": 30,
  "height": 1.6
}
{
  "_id": ObjectId("56b79abb2464ce3e718b254d"),
  "name": "Raichu",
  "description": "Eletric",
  "attack": 50,
  "defense": 30,
  "heigth": 0.8
}
{
  "_id": ObjectId("56b79abb2464ce3e718b254e"),
  "name": "Sandshrew",
  "description": "Ground",
  "attack": 40,
  "defense": 40,
  "heigth": 0.6
}
{
  "_id": ObjectId("56b79abb2464ce3e718b254f"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("56b79ac32464ce3e718b2550"),
  "name": "Serperior",
  "description": "Grass",
  "attack": 40,
  "defense": 40,
  "heigth": 3.3
}
Fetched 5 record(s) in 10ms

```

## 6. Procurando Pokemon Wurmple
### Atribuindo o cursor para uma variavel para altera-lo futuramente
``` 
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne({name: "Serperior"})

```

## 7. Atualização da propiedade para Fight
``` 
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> poke.description = "Ele é um tipo Grass"
Ele é um tipo Grass
MACBEPIDUCB174(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 6ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```