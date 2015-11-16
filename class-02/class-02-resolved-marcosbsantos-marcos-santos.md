##MongoDB -Aula2- Exercícios
##autor: MARCOS SANTOS

##Crie uma base chamada be-mean-pokemons:

 > use be-mean-pokemons
switched to db be-mean-pokemons

##Liste quais databases você possui neste servidor:

> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
teste              0.078GB

##Liste quais coleções você possui nesta base:

> show collections
> 

##Insira 5 pokemons a sua escolha:

db.pokemons.save({'name':'Magcargo','description':'Este Pokémon retorna ao seu tamanho original mergulhando-se no magma.','attack':30,'defense':50
,'height':0.8})

db.pokemons.save({'name':'Swinub','description':'Sua comida favorita é um cogumelo que cresce sob a cobertura de grama morta.','attack':30,'defense':20,'height':0.4})

db.pokemons.save({'name':'Piloswine','description':'É coberta por uma espessa camada de cabelos compridos que lhe permite suportar o frio congelante.','attack':50,'defense':40,'height':1.1})

db.pokemons.save({'name':'Corsola','description':'Se qualquer ramo quebra, este Pokémon cresce de volta em apenas uma noite..','attack':30,'defense':40
,'height':0.6})

db.pokemons.save({'name':'Remoraid','description':' Quando a evolução se aproxima, este Pokémon viaja a jusante dos rios.','attack':30,'defense':20
,'height':0.6})

##Liste os pokemons existentes na sua coleção:

> db.pokemons.find()
{ "_id" : ObjectId("56490978055d13b8416e9c63"), "name" : "Magcargo", "description" : "Este Pokémon retorna ao seu tamanho original mergulhando-se no magma.", "attack" : 30, "defense" : 50, "height" : 0.8 }
{ "_id" : ObjectId("56490a26055d13b8416e9c64"), "name" : "Remoraid", "description" : " Quando a evolução se aproxima, este Pokémon viaja a jusante dos rios.", "attack" : 30, "defense" : 20, "height" : 0.6 }
{ "_id" : ObjectId("56490a30055d13b8416e9c65"), "name" : "Corsola", "description" : "Se qualquer ramo quebra, este Pokémon cresce de volta em apenas uma noite..", "attack" : 30, "defense" : 40, "height" : 0.6 }
{ "_id" : ObjectId("56490a38055d13b8416e9c66"), "name" : "Piloswine", "description" : "É coberta por uma espessa camada de cabelos compridos que lhe permite suportar o frio congelante.", "attack" : 50, "defense" : 40, "height" : 1.1 }
{ "_id" : ObjectId("56490a49055d13b8416e9c67"), "name" : "Swinub", "description" : "Sua comida favorita é um cogumelo que cresce sob a cobertura de grama morta.", "attack" : 30, "defense" : 20, "height" : 0.4 }

##Liste um pokemon a sua escolha e armazene-o em uma variável chamada "poke":

> var poke = db.pokemons.findOne({'name' : 'Piloswine'})
> poke
{
	"_id" : ObjectId("56490a38055d13b8416e9c66"),
	"name" : "Piloswine",
	"description" : "É coberta por uma espessa camada de cabelos compridos que lhe permite suportar o frio congelante.",
	"attack" : 50,
	"defense" : 40,
	"height" : 1.1
}

##Modifique sua 'description' e salve!

> poke.description
É coberta por uma espessa camada de cabelos compridos que lhe permite suportar o frio congelante.
> poke.description = 'Possui cabelo bem curto por conta do calor do NE do Brasil'
Possui cabelo bem curto por conta do calor do NE do Brasil
> poke.description
Possui cabelo bem curto por conta do calor do NE do Brasil
> poke
{
	"_id" : ObjectId("56490a38055d13b8416e9c66"),
	"name" : "Piloswine",
	"description" : "Possui cabelo bem curto por conta do calor do NE do Brasil",
	"attack" : 50,
	"defense" : 40,
	"height" : 1.1
}
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find()
{ "_id" : ObjectId("56490978055d13b8416e9c63"), "name" : "Magcargo", "description" : "Este Pokémon retorna ao seu tamanho original mergulhando-se no magma.", "attack" : 30, "defense" : 50, "height" : 0.8 }
{ "_id" : ObjectId("56490a26055d13b8416e9c64"), "name" : "Remoraid", "description" : " Quando a evolução se aproxima, este Pokémon viaja a jusante dos rios.", "attack" : 30, "defense" : 20, "height" : 0.6 }
{ "_id" : ObjectId("56490a30055d13b8416e9c65"), "name" : "Corsola", "description" : "Se qualquer ramo quebra, este Pokémon cresce de volta em apenas uma noite..", "attack" : 30, "defense" : 40, "height" : 0.6 }
{ "_id" : ObjectId("56490a38055d13b8416e9c66"), "name" : "Piloswine", "description" : "Possui cabelo bem curto por conta do calor do NE do Brasil", "attack" : 50, "defense" : 40, "height" : 1.1 }
{ "_id" : ObjectId("56490a49055d13b8416e9c67"), "name" : "Swinub", "description" : "Sua comida favorita é um cogumelo que cresce sob a cobertura de grama morta.", "attack" : 30, "defense" : 20, "height" : 0.4 }
