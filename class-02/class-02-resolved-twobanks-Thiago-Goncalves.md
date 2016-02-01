# MongoDB - Aula 02 - Exercício
autor: Thiago Gonçalves 

## Crie uma database chamada be-mean-pokemons; (passo 1)

> use be-mean-pokemons <br>
switched to db be-mean-pokemons

## Listagem das databases (passo 2)

> show dbs
be-mean            0.004GB <br>
be-mean-instagram  0.000GB <br>
local              0.000GB

## Listagem das coleções (passo 3)

> show collections

## Cadastro dos pokemons (passo 4)

> var pokemon = {'name':'Arbok','description':'Cobra','type':'cobra','attack': 40,'height':3.5}
> db.pokemons.insert(pokemon) <br>
> var pokemon = {'name':'Togepi','description':'Spike Ball','type':'ovo','attack': 10,'height':0.3}
> db.pokemons.insert(pokemon) <br>
> var pokemon = {'name':'Jigglypuff','description':'Balloon','type':'fofo','attack': 20,'height':0.5}
> db.pokemons.insert(pokemon) <br>
> var pokemon = {'name':'Meowth','description':'Gato','type':'gato','attack': 20,'height':0.4}
> db.pokemons.insert(pokemon) <br>
> var pokemon = {'name':'Psyduck','description':'Pato','type':'pato','attack': 30,'height':0.8}
> db.pokemons.insert(pokemon) <br>
> var pokemon = {'name':'Chansey','description':'Saúde','type':'ovo','attack': 10,'height':1.1}
> db.pokemons.insert(pokemon) <br>

## Lista dos pokemons (passo 5)

> db.pokemons.find()
{ "_id" : ObjectId("56a562a889a280b6f04c7677"), "name" : "Arbok", "description" : "Cobra", "type" : "cobra", "attack" : 40, "height" : 3.5 } <br>
{ "_id" : ObjectId("56a562be89a280b6f04c7678"), "name" : "Togepi", "description" : "Spike Ball", "type" : "ovo", "attack" : 10, "height" : 0.3 } <br>
{ "_id" : ObjectId("56a5630389a280b6f04c7679"), "name" : "Jigglypuff", "description" : "Balloon", "type" : "fofo", "attack" : 20, "height" : 0.5 } <br>
{ "_id" : ObjectId("56a5632d89a280b6f04c767a"), "name" : "Meowth", "description" : "Gato", "type" : "gato", "attack" : 20, "height" : 0.4 } <br>
{ "_id" : ObjectId("56a5635089a280b6f04c767b"), "name" : "Psyduck", "description" : "Pato", "type" : "pato", "attack" : 30, "height" : 0.8 } <br>
{ "_id" : ObjectId("56a5638289a280b6f04c767c"), "name" : "Chansey", "description" : "Saúde", "type" : "ovo", "attack" : 10, "height" : 1.1 } <br>


## Pokemon (passo 6)

> var poke = db.pokemons.findOne({nome:'Psyduck'}) <br>
> poke <br>
{
	"_id" : ObjectId("56a5635089a280b6f04c767b"),
	"nome" : "Psyduck",
	"descricao" : "Pato",
	"tipo" : "pato",
	"ataque" : 30,
	"altura" : 0.8
}

## Atualização do Pokemon (passo 6)

> poke.descricao = "Pato chapado de doce" <br>
Pato chapado de doce <br>
> db.pokemons.save(poke) <br>
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
