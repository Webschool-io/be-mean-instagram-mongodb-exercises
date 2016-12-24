# MongoDB - Aula 02 - Exercício
autor: Samuel Desconsi - Underzzoo

##	1. Crie uma database chamada be-mean-pokemons

    ```
    > use be-mean-pokemons
	switched to db be-mean-pokemons
	> var pokemon = {'name': 'Pikachu', 'description': 'Rato Elétrico', 'type': 'Electric', attack: 55, height: 0.4}
	> db.pokemons.insert(pokemon)
	WriteResult({ "nInserted" : 1 })

    ```

## 	2.	Liste quais databases você possui nesse servidor

    ```
	> show dbs
	be-mean-instagram  0.000GB
	be-mean-pokemons   0.000GB
	local              0.000GB
	pokemons           0.000GB
	>
    ```
## 	3.	Liste quais coleções você possui nessa database;

	```
	> show collections
	pokemons
	>
	```
	
## 4.	Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

    ```
var pokemons = [
{
	name: 'Bulbasaur', 
	description: 'Couve-Flor', 
	type: 'Grass', 
	attack: 30, 
	height: 0.7}, 
{
	name: 'Charmander', 
	description: 'Dragãozinho', 
	type: 'Fire', 
	attack: 30, 
	height: 0.6}, 
{
	name: 'Squirtle', 
	description: 'Tartaruguinha', 
	type: 'Water', 
	attack: 30, 
	height: 0.5}, 
{
	name: 'Caterpie', 
	description: 'Corózinho', 
	type: 'Bug', 
	attack: 20, height: 0.3}, 
{
	name: 'Butterfree', 
	description: 'Corózinho Evoluido pra brabuleta', 
	type: 'Bug', 
	attack: 20, 
	height: 1.1}
]

> db.pokemons.insert(pokemons)
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 5,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})


    ```    
## 	5.	Liste os pokemons existentes na sua coleção

    ```
     > db.pokemons.find()
	{ "_id" : ObjectId("577530b35bb4daceabe68462"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "Electric", "attack" : 55, "height" : 0.4 }
	{ "_id" : ObjectId("577532fa5bb4daceabe68463"), "name" : "Bulbasaur", "description" : "Couve-Flor", "type" : "Grass", "attack" : 30, "height" : 0.7 }
	{ "_id" : ObjectId("5775330e5bb4daceabe68464"), "name" : "Charmander", "description" : "Dragãozinho", "type" : "Fire", "attack" : 30, "height" : 0.6 }
	{ "_id" : ObjectId("5775331a5bb4daceabe68465"), "name" : "Squirtle", "description" : "Tartaruguinha", "type" : "Water", "attack" : 30, "height" : 0.5 }
	{ "_id" : ObjectId("577533245bb4daceabe68466"), "name" : "Caterpie", "description" : "Corózinho", "type" : "Bug", "attack" : 20, "height" : 0.3 }
	{ "_id" : ObjectId("5775332d5bb4daceabe68467"), "name" : "Caterpie", "description" : "Corózinho", "type" : "Bug", "attack" : 20, "height" : 0.3 }
    ```   
	
## 	6.	Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`

    ```                                                                          
> var query = {name: 'Charmander'}
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("57ef3df2af51dbefcb776aad"),
	"name" : "Charmander",
	"description" : "Dragãozinho",
	"type" : "Fire",
	"attack" : 30,
	"height" : 0.6
}

```

## 	7.	Modifique sua `description` e salvê-o

```
> poke.description = "Dragão do rabo fogoso"
Dragão do rabo fogoso
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find().pretty()
{
	"_id" : ObjectId("57ef3df2af51dbefcb776aac"),
	"name" : "Bulbasaur",
	"description" : "Couve-Flor",
	"type" : "Grass",
	"attack" : 30,
	"height" : 0.7
}
{
	"_id" : ObjectId("57ef3df2af51dbefcb776aad"),
	"name" : "Charmander",
	"description" : "Dragão do rabo fogoso",
	"type" : "Fire",
	"attack" : 30,
	"height" : 0.6
}
{
	"_id" : ObjectId("57ef3df2af51dbefcb776aae"),
	"name" : "Squirtle",
	"description" : "Tartaruguinha",
	"type" : "Water",
	"attack" : 30,
	"height" : 0.5
}
{
	"_id" : ObjectId("57ef3df2af51dbefcb776aaf"),
	"name" : "Caterpie",
	"description" : "Corózinho",
	"type" : "Bug",
	"attack" : 20,
	"height" : 0.3
}
{
	"_id" : ObjectId("57ef3df2af51dbefcb776ab0"),
	"name" : "Butterfree",
	"description" : "Corózinho Evoluido pra brabuleta",
	"type" : "Bug",
	"attack" : 20,
	"height" : 1.1
}

```
