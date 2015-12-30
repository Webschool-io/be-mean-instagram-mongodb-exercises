# MongoDB - Aula 02 - Exercício
autor: Nicholas Fernandes de Almeida Paolillo
## Criar database própria (passo 1)
```
use be-mean-pokemons
switched to db be-mean-pokemons
```
## Listagem das databases (passo 2)
```
be-mean-pokemons> show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
local             → 0.000GB
```
## Cadastro dos pokemons (passo 4)
```
var pokemon = {'name':'venusaur','description':'Dinossauro Mutante Gigante pai, ancestral das tartarugas ninjas','type': 'leaf', attack: 82, height: 20 , 'defense':83}
db.pokemons.save(pokemon)
Inserted 1 record(s) in 285ms
WriteResult({
  "nInserted": 1
})
var pokemon = {'name':'charizard','description':'Dinossauro Mutante Gigante Voador Cospe Fogo, evolução do charmander','type': 'fire', attack: 84, height: 17 , 'defense':78}
db.pokemons.save(pokemon)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})
var pokemon = {'name':'blastoise','description':'Tartaruga Mutante Gigante Nadadora Cospe Água, evolução do squirtle, ancestral do Mandu','type': 'water', attack: 83, height: 16 , 'defense':100}
db.pokemons.save(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
var pokemon = {'name':'butterfree','description':'Borboleta que voa, evolução do catterpie','type': 'leaf', attack: 45, height: 11 , 'defense':50}
db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

var pokemon = {'name':'raichu','description':'Ratazana elétrica tipo Itaipu','type': 'electric', attack: 90, height: 8 , 'defense':55}
db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
var pokemon = {'name':'dugtrio','description':'Sociedade de minhocas mutantes engraçadas','type': 'earth', attack: 80, height: 7 , 'defense':50}
db.pokemons.save(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
var pokemon = {'name':'psyduck','description':'Pato com forte enxaqueca e poderes similares ao Charles Xavier','type': 'water-psychic', attack: 52, height: 8 , 'defense':48}
db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```
## A volta do passo 2 Listagem das databases (passo 2)
```
be-mean-pokemons> show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
be-mean-pokemons  → 0.000GB
local             → 0.000GB
```
## Listagem das coleções (passo 3)
```
be-mean-pokemons> show collections
pokemnos → 0.000MB / 0.016MB
pokemons → 0.001MB / 0.035MB
## Lista dos pokemons (passo 5)
```
```
be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56785f5db851c1d5742cb994"),
  "name": "venusaur",
  "description": "Dinossauro Mutante Gigante pai, ancestral das tartarugas ninjas",
  "type": "leaf",
  "attack": 82,
  "height": 20,
  "defense": 83
}
{
  "_id": ObjectId("5678620ab851c1d5742cb997"),
  "name": "charizard",
  "description": "Dinossauro Mutante Gigante Voador Cospe Fogo, evolução do charmander",
  "type": "fire",
  "attack": 84,
  "height": 17,
  "defense": 78
}
{
  "_id": ObjectId("56786220b851c1d5742cb998"),
  "name": "blastoise",
  "description": "Tartaruga Mutante Gigante Nadadora Cospe Água, evolução do squirtle, ancestral do Mandu",
  "type": "water",
  "attack": 83,
  "height": 16,
  "defense": 100
}
{
  "_id": ObjectId("5678624fb851c1d5742cb999"),
  "name": "butterfree",
  "description": "Borboleta que voa, evolução do catterpie",
  "type": "leaf",
  "attack": 45,
  "height": 11,
  "defense": 50
}
{
  "_id": ObjectId("56786266b851c1d5742cb99a"),
  "name": "raichu",
  "description": "Ratazana elétrica tipo Itaipu",
  "type": "electric",
  "attack": 90,
  "height": 8,
  "defense": 55
}
{
  "_id": ObjectId("56786288b851c1d5742cb99b"),
  "name": "dugtrio",
  "description": "Sociedade de minhocas mutantes engraçadas",
  "type": "earth",
  "attack": 80,
  "height": 7,
  "defense": 50
}
{
  "_id": ObjectId("5678629eb851c1d5742cb99c"),
  "name": "psyduck",
  "description": "Pato com forte enxaqueca e poderes similares ao Charles Xavier",
  "type": "water-psychic",
  "attack": 52,
  "height": 8,
  "defense": 48
}
```
## QUERY pelo pokemon(passo 6)
```
be-mean-pokemons> var query = {"attack":90}
```
```
be-mean-pokemons> var poke = db.pokemons.findOne(query)
```
```
be-mean-pokemons> poke
{
  "_id": ObjectId("56786266b851c1d5742cb99a"),
  "name": "raichu",
  "description": "Ratazana elétrica tipo Itaipu",
  "type": "electric",
  "attack": 90,
  "height": 8,
  "defense": 55
}
```
## Mudança de Habilidade (passo 7)
```
be-mean-pokemons> poke.defense
55
```
```
be-mean-pokemons> poke.defense = 60
60
```
```
be-mean-pokemons> poke
{
  "_id": ObjectId("56786266b851c1d5742cb99a"),
  "name": "raichu",
  "description": "Ratazana elétrica tipo Itaipu",
  "type": "electric",
  "attack": 90,
  "height": 8,
  "defense": 60
}
```
## Salvando no database as mudanças (passo 8)
```
be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
