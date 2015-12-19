Exercicio Aula 04

#Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbasaur e Charmander.
 var query = {name : {$in: [/pikachu/i, /squirtle/i, /bulbasaur/i, /charmander/i]}}
 var mod = {$pushAll: {ataques : ['soco', 'chute']}}
 var options = {multi: 1}
 db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

 db.pokemons.find(query)
{
  "_id" : ObjectId("564c920851464aa7fe338b09"),
  "name" : "Charmander",
  "type" : "Fire",
  "description" : "dragaozin gente fina",
  "height" : 0.6,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ]
}
{
  "_id" : ObjectId("564c921951464aa7fe338b0a"),
  "name" : "Bulbasaur",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ]
}
{
  "_id" : ObjectId("564c922251464aa7fe338b0b"),
  "name" : "Squirtle",
  "type" : "Water",
  "description" : "tartaruga que joga agua",
  "height" : 0.5,
  "defense" : 30,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ]
}
{
  "_id" : ObjectId("564c924e51464aa7fe338b0c"),
  "name" : "Pikachu",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 40,
  "ataques" : [ "soco", "chute" ]
}

#Adicionar 1 movimento em todos os pokemons ("desvio").

 var query = {}
 var mod = {$push: {movimento : 'desvio'}}
 db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 10, "nUpserted" : 0, "nModified" : 10 })

 db.pokemons.find(query)
{
  "_id" : ObjectId("564c920851464aa7fe338b09"),
  "name" : "Charmander",
  "type" : "Fire",
  "description" : "dragaozin gente fina",
  "height" : 0.6,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c921951464aa7fe338b0a"),
  "name" : "Bulbasaur",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c922251464aa7fe338b0b"),
  "name" : "Squirtle",
  "type" : "Water",
  "description" : "tartaruga que joga agua",
  "height" : 0.5,
  "defense" : 30,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c924e51464aa7fe338b0c"),
  "name" : "Pikachu",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 40,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c9ede1b4297cea8cfdfaf"),
  "name" : "Dedenne",
  "type" : "Electric",
  "description" : "rato gordinho de energia",
  "height" : 0.2,
  "defense" : 30,
  "attack" : 30,
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c9f4d1b4297cea8cfdfb0"),
  "name" : "Eelektrik",
  "type" : "Electric",
  "description" : "minhoca eletrica",
  "height" : 1.2,
  "defense" : 40,
  "attack" : 30,
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c9f9b1b4297cea8cfdfb1"),
  "name" : "Corphish",
  "type" : "Water",
  "description" : "caranguejo mais ou menos",
  "height" : 0.6,
  "defense" : 40,
  "attack" : 30,
  "movimento" : [ "desvio" ]
}
{
   "_id" : ObjectId("564c9fe81b4297cea8cfdfb2"),
   "name" : "Magmortar",
   "type" : "Fire",
   "description" : "gordo cheio de fogo",
   "height" : 1.6,
   "defense" : 50,
   "attack" : 30,
   "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564ca08a1b4297cea8cfdfb4"),
  "name" : "Ninetales",
  "type" : "Fire",
  "description" : "raposa que parece pavao",
  "height" : 1.1,
  "defense" : 40,
  "attack" : 30,
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564ca2381b4297cea8cfdfb6"),
  "name" : "Crobat",
  "type" : "Poison",
  "description" : "morcego rapido pra carai",
  "height" : 1.8,
  "defense" : 50,
  "attack" : 40,
  "movimento" : [ "desvio" ]
}


#Adicionar o pokemon "AindaNaoExisteMon" caso ele não exista com todos os dados com o valor "null" e a descrição "Sem maiores informações".
 var query = {name: /aindanaoexistemon/i}
 var mod = {$set: {name: "AindaNaoExisteMon", type: null, description: "Sem mais informações", height: null, defense: null, attack:null}}
 mod
{
        "$set" : {
                "name" : "AindaNaoExisteMon",
                "type" : null,
                "description" : "Sem mais informações",
                "height" : null,
                "defense" : null,
                "attack" : null
        }
}

 var options = {upsert: true}
 db.pokemons.update(query, mod, options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("564cacc53422234f9e3a59a1")
})

 var query = {name: /aindanaoexistemon/i}
 db.pokemons.find(query)
{
  "_id" : ObjectId("564cacc53422234f9e3a59a1"),
  "name" : "AindaNaoExisteMon",
  "type" : null,
  "description" : "Sem mais informações",
  "height" : null,
  "defense" : null,
  "attack" : null
}

#Pesquisar todos os pokemons que possuam o ataque "investida" e mais um que voce adicionou, escolha seu pokemon favorito.

 var query = {ataques : {$all: ['investida', 'soco']}}
 db.pokemons.find(query)
{
  "_id" : ObjectId("564c920851464aa7fe338b09"),
  "name" : "Charmander",
  "type" : "Fire",
  "description" : "dragaozin gente fina",
  "height" : 0.6,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute", "investida" ],
  "movimento" : [ "desvio" ]
}

#Pesquisar todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

 var query = {ataques : {$all: ['chute']}}
 db.pokemons.find(query)
{
  "_id" : ObjectId("564c920851464aa7fe338b09"),
  "name" : "Charmander",
  "type" : "Fire",
  "description" : "dragaozin gente fina",
  "height" : 0.6,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute", "investida" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c921951464aa7fe338b0a"),
  "name" : "Bulbasaur",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c922251464aa7fe338b0b"),
  "name" : "Squirtle",
  "type" : "Water",
  "description" : "tartaruga que joga agua",
  "height" : 0.5,
  "defense" : 30,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c924e51464aa7fe338b0c"),
  "name" : "Pikachu",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 40,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}

#Pesquisar todos os que não são do tipo eletrico.

 var query = {type : {$ne: 'Electric'}}
 db.pokemons.find(query)
{
  "_id" : ObjectId("564c920851464aa7fe338b09"),
  "name" : "Charmander",
  "type" : "Fire",
  "description" : "dragaozin gente fina",
  "height" : 0.6,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute", "investida" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c921951464aa7fe338b0a"),
  "name" : "Bulbasaur",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c922251464aa7fe338b0b"),
  "name" : "Squirtle",
  "type" : "Water",
  "description" : "tartaruga que joga agua",
  "height" : 0.5,
  "defense" : 30,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c924e51464aa7fe338b0c"),
  "name" : "Pikachu",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 40,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c9f9b1b4297cea8cfdfb1"),
  "name" : "Corphish",
  "type" : "Water",
  "description" : "caranguejo mais ou menos",
  "height" : 0.6,
  "defense" : 40,
  "attack" : 30,
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c9fe81b4297cea8cfdfb2"),
  "name" : "Magmortar",
  "type" : "Fire",
  "description" : "gordo cheio de fogo",
  "height" : 1.6,
  "defense" : 50,
  "attack" : 30,
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564ca08a1b4297cea8cfdfb4"),
  "name" : "Ninetales",
  "type" : "Fire",
  "description" : "raposa que parece pavao",
  "height" : 1.1,
  "defense" : 40,
  "attack" : 30,
  "movimento" : [ "desvio" ],
  "ataques" : [ "investida" ]
}
{
  "_id" : ObjectId("564ca2381b4297cea8cfdfb6"),
  "name" : "Crobat",
  "type" : "Poison",
  "description" : "morcego rapido pra carai",
  "height" : 1.8,
  "defense" : 50,
  "attack" : 40,
  "movimento" : [ "desvio" ],
  "ataques" : [ "investida" ]
}
{
  "_id" : ObjectId("564cacc53422234f9e3a59a1"),
  "name" : "AindaNaoExisteMon",
  "type" : null,
  "description" : "Sem mais informações",
  "height" : null,
  "defense" : null,
  "attack" : null
}

#Pesquisar todos pokemons que tenham o ataque investida e que que tenham a defesa !<= a 49.

 var query = {ataques : {$eq: 'chute'}, defense : {$lte : 49}}
 db.pokemons.find(query)
{
  "_id" : ObjectId("564c920851464aa7fe338b09"),
  "name" : "Charmander",
  "type" : "Fire",
  "description" : "dragaozin gente fina",
  "height" : 0.6,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute", "investida" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c921951464aa7fe338b0a"),
  "name" : "Bulbasaur",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c922251464aa7fe338b0b"),
  "name" : "Squirtle",
  "type" : "Water",
  "description" : "tartaruga que joga agua",
  "height" : 0.5,
  "defense" : 30,
  "attack" : 30,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}
{
  "_id" : ObjectId("564c924e51464aa7fe338b0c"),
  "name" : "Pikachu",
  "type" : "Grass",
  "description" : "perereca com cipo",
  "height" : 0.7,
  "defense" : 20,
  "attack" : 40,
  "ataques" : [ "soco", "chute" ],
  "movimento" : [ "desvio" ]
}

#Remova todos os pokemons do tipo agua e com ataque menor que 50

 var query = {type : {$eq: 'Water'}, defense : {$lt : 50}}
 db.pokemons.remove(query)
WriteResult({ "nRemoved" : 2 })
