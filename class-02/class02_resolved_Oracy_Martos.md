# MongoDB - Aula 01 - Exercício
Autor: Oracy Martos

Be-mean

# 1- Criar Database
```
> use be_mean_pokemons
switched to db be_mean_pokemons
```

# 2- Listar Databases
```
> show dbs
bemean  0.078GB
local   0.078GB
test    0.078GB
```

# 3- Listar collections
```
> show collections
empresas
pokemons
projects
projetos
system.indexes
teste
users
```
# 4- Criar e inserir 5 pokemons
```
var pokemon = {'name':'Gardevoir', 'description':'Pokemon gay que voa', attack: 79, defense: 30, height: 0.5}
var pokemon = {'name':'Mew', 'description':'Pokemon gay que voa também e rosa', attack: 150, defense: 130, height: 0.4}
var pokemon = {'name':'Rayquaza', 'description':'Pokemon elétrico forte', attack: 160, defense: 100, height: 1.5}
var pokemon = {'name':'Emboar', 'description':'Pokemon lança chamas', attack: 95, defense: 45, height: 0.7}
var pokemon = {'name':'Golduck', 'description':'Pokemon evolução do pato chato', attack: 59, defense: 31, height: 0.6}
```
```
> var pokemon = {'name':'Gardevoir', 'description':'Pokemon gay que voa', attack: 79, defense: 30, height: 0.5}
> db.be_mean_pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = {'name':'Mew', 'description':'Pokemon gay que voa também e rosa', attack: 150, defense: 130, height: 0.4}
> db.be_mean_pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = {'name':'Rayquaza', 'description':'Pokemon elétrico forte', attack: 160, defense: 100, height: 1.5}
> db.be_mean_pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = {'name':'Emboar', 'description':'Pokemon lança chamas', attack: 95, defense: 45, height: 0.7}
> db.be_mean_pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = {'name':'Golduck', 'description':'Pokemon evolução do pato chato', attack: 59, defense: 31, height: 0.6}
> db.be_mean_pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })`
```

# 5- Listar os Pokemons
```
> db.be_mean_pokemons.find().pretty()
{
	"_id" : ObjectId("58ba28a79a581ace63e5af45"),
	"name" : "Gardevoir",
	"description" : "Pokemon gay que voa",
	"attack" : 79,
	"defense" : 30,
	"height" : 0.5
}
{
	"_id" : ObjectId("58ba28b69a581ace63e5af46"),
	"name" : "Gardevoir",
	"description" : "Pokemon gay que voa",
	"attack" : 79,
	"defense" : 30,
	"height" : 0.5
}
{
	"_id" : ObjectId("58ba28bd9a581ace63e5af47"),
	"name" : "Mew",
	"description" : "Pokemon gay que voa também e rosa",
	"attack" : 150,
	"defense" : 130,
	"height" : 0.4
}
{
	"_id" : ObjectId("58ba28c49a581ace63e5af48"),
	"name" : "Rayquaza",
	"description" : "Pokemon elétrico forte",
	"attack" : 160,
	"defense" : 100,
	"height" : 1.5
}
{
	"_id" : ObjectId("58ba28cd9a581ace63e5af49"),
	"name" : "Emboar",
	"description" : "Pokemon lança chamas",
	"attack" : 95,
	"defense" : 45,
	"height" : 0.7
}
{
	"_id" : ObjectId("58ba28d29a581ace63e5af4a"),
	"name" : "Golduck",
	"description" : "Pokemon evolução do pato chato",
	"attack" : 59,
	"defense" : 31,
	"height" : 0.6
}
```

# 6- Buscar 1 pokemon pelo nome e armazenar em uma variável.
```
> var poke = db.be_mean_pokemons.findOne({name: 'Emboar'})
> poke.name
Emboar`
```

# 7- Alterar a description, e salvar a nova description.
```
> poke.description = 'Fogo no rabo'
Fogo no rabo
> db.be_mean_pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```