MongoDB - Aula 04 - Exercício

autor: Jackell Alves

Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /Bulbasaur/i}, {name: /charmander/i}]}
db.pokemon.find(query)
var mod = {$pushAll: {moves: ['ataque rápido', 'investida']}}
var options = {multi: true}
db.pokemon.update(query, mod, options)
db.pokemon.find(query)
{ "_id" : ObjectId("5644b144fc24cdcda5d10cdb"), "name" : "Bulbasaur", "description" : "Há uma semente em suas costas.", "type" : "Grama", "attack" : 49, "defense" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida" ] }
{ "_id" : ObjectId("5644b7d9fc24cdcda5d10cdd"), "name" : "Pikachu", "description" : "Sempre que Pikachu se depara com algo novo, que explode com um choque de eletricidade.", "type" : "Mouse", "attack" : 55, "defense" : 40, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida" ] }
{ "_id" : ObjectId("564e00a25f3a3c1fc9fcab63"), "name" : "charmander", "description" : "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.", "type" : "fire", "attack" : 52, "defense" : 43, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida" ] }
{ "_id" : ObjectId("564dffef5f3a3c1fc9fcab62"), "name" : "squirtle", "description" : "Shell de Squirtle não é apenas usado para a proteção.", "type" : "Water", "attack" : 48, "defense" : 65, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida" ] }

Adicionar 1 movimento em todos os pokemons: desvio.
{ "_id" : ObjectId("564372ef821ac90657925b7c"), "name" : "Paras", "description" : "Paras tem cogumelos parasitas que crescem em sua parte traseira chamado tochukaso.", "type" : "Mushroom", "attack" : 70, "defense" : 55, "height" : 0.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564373da821ac90657925b7d"), "name" : "Golbat", "description" : "Golbat ama beber o sangue de seres vivos.", "type" : "Bat", "attack" : 80, "defense" : 70, "height" : 1.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643741c821ac90657925b7e"), "name" : "Clefairy", "description" : "Em cada noite de lua cheia, grupos deste Pokémon sair para jogar.", "type" : "fada", "attack" : 45, "defense" : 48, "height" : 0.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643745a821ac90657925b7f"), "name" : "Nidoqueen", "description" : "Este Pokémon está mais forte quando se está defendendo seus filhotes.", "type" : "Drill", "attack" : 92, "defense" : 87, "height" : 1.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643748f821ac90657925b80"), "name" : "Sandshrew", "description" : "Este Pokémon se enrola para se proteger de seus inimigos.", "type" : "Mouse", "attack" : 75, "defense" : 85, "height" : 0.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564374d1821ac90657925b81"), "name" : "Arbok", "description" : "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo.", "type" : "cobra", "attack" : 85, "defense" : 69, "height" : 3.5, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5644b144fc24cdcda5d10cdb"), "name" : "Bulbasaur", "description" : "Há uma semente em suas costas.", "type" : "Grama", "attack" : 49, "defense" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("5644b7ebfc24cdcda5d10cde"), "name" : "Pikachu", "description" : "Sempre que Pikachu se depara com algo novo, que explode com um choque de eletricidade.", "type" : "Mouse", "attack" : 55, "defense" : 40, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564e00a25f3a3c1fc9fcab63"), "name" : "charmander", "description" : "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.", "type" : "fire", "attack" : 52, "defense" : 43, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564dffef5f3a3c1fc9fcab62"), "name" : "squirtle", "description" : "Shell de Squirtle não é apenas usado para a proteção.", "type" : "Water", "attack" : 48, "defense" : 65, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }

Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
var query = {name: /AindaNaoExisteMon/i}
var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null}, }
var options = {upsert: true}
db.pokemon.update(query, mod, options)
WriteResult({
    "nMatched" : 0,
    "nUpserted" : 1,
    "nModified" : 0,
    "_id" : ObjectId("564dbc99c6d924a2d59c4ae2")
})
db.pokemon.find(query)
{ "_id" : ObjectId("564dbc99c6d924a2d59c4ae2"), "name" : "AindaNaoExisteMon", "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null }

Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
var query = {moves: {$in: [/ataque rápido/i, /investida/i]}}
db.pokemons.find(query)
{ "_id" : ObjectId("5644b7ebfc24cdcda5d10cde"), "name" : "Pikachu", "description" : "Sempre que Pikachu se depara com algo novo, que explode com um choque de eletricidade.", "type" : "Mouse", "attack" : 55, "defense" : 40, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564e00a25f3a3c1fc9fcab63"), "name" : "charmander", "description" : "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.", "type" : "fire", "attack" : 52, "defense" : 43, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564dffef5f3a3c1fc9fcab62"), "name" : "squirtle", "description" : "Shell de Squirtle não é apenas usado para a proteção.", "type" : "Water", "attack" : 48, "defense" : 65, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }

Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
var query = {moves: {$in: [/ataque rápido/i, /investida/i, /desvio/i]}}
db.pokemons.find(query)
{ "_id" : ObjectId("5644b1b9fc24cdcda5d10cdc"), "name" : "Bulbasaur", "description" : "Há uma semente em suas costas.", "type" : "Grama", "attack" : 49, "defense" : 49, "height" : 0.7, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("5644b7d9fc24cdcda5d10cdd"), "name" : "Pikachu", "description" : "Sempre que Pikachu se depara com algo novo, que explode com um choque de eletricidade.", "type" : "Mouse", "attack" : 55, "defense" : 40, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("5644b7ebfc24cdcda5d10cde"), "name" : "Pikachu", "description" : "Sempre que Pikachu se depara com algo novo, que explode com um choque de eletricidade.", "type" : "Mouse", "attack" : 55, "defense" : 40, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564e00a25f3a3c1fc9fcab63"), "name" : "charmander", "description" : "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.", "type" : "fire", "attack" : 52, "defense" : 43, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }

Pesquisar todos os pokemons que não são do tipo elétrico.
var query = {type: {$ne: 'elétrico'}}
db.pokemons.find(query)
{ "_id" : ObjectId("564372ef821ac90657925b7c"), "name" : "Paras", "description" : "Paras tem cogumelos parasitas que crescem em sua parte traseira chamado tochukaso.", "type" : "Mushroom", "attack" : 70, "defense" : 55, "height" : 0.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564373da821ac90657925b7d"), "name" : "Golbat", "description" : "Golbat ama beber o sangue de seres vivos.", "type" : "Bat", "attack" : 80, "defense" : 70, "height" : 1.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643741c821ac90657925b7e"), "name" : "Clefairy", "description" : "Em cada noite de lua cheia, grupos deste Pokémon sair para jogar.", "type" : "fada", "attack" : 45, "defense" : 48, "height" : 0.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643745a821ac90657925b7f"), "name" : "Nidoqueen", "description" : "Este Pokémon está mais forte quando se está defendendo seus filhotes.", "type" : "Drill", "attack" : 92, "defense" : 87, "height" : 1.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643748f821ac90657925b80"), "name" : "Sandshrew", "description" : "Este Pokémon se enrola para se proteger de seus inimigos.", "type" : "Mouse", "attack" : 75, "defense" : 85, "height" : 0.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564374d1821ac90657925b81"), "name" : "Arbok", "description" : "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo.", "type" : "cobra", "attack" : 85, "defense" : 69, "height" : 3.5, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5644b144fc24cdcda5d10cdb"), "name" : "Bulbasaur", "description" : "Há uma semente em suas costas.", "type" : "Grama", "attack" : 49, "defense" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("5644b7ebfc24cdcda5d10cde"), "name" : "Pikachu", "description" : "Sempre que Pikachu se depara com algo novo, que explode com um choque de eletricidade.", "type" : "Mouse", "attack" : 55, "defense" : 40, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564e00a25f3a3c1fc9fcab63"), "name" : "charmander", "description" : "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.", "type" : "fire", "attack" : 52, "defense" : 43, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564dffef5f3a3c1fc9fcab62"), "name" : "squirtle", "description" : "Shell de Squirtle não é apenas usado para a proteção.", "type" : "Water", "attack" : 48, "defense" : 65, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564e0421f18f5576b6d565fd"), "name" : "AindaNaoExisteMon", "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null }

Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
var query = {$and: [{moves: {$in: ['investida']}}, {defense: {lte: 49}}]}
db.pokemons.find(query)
>

Remova todos os pokemons do tipo água e com attack menor que 50.
var query = {$and: [{type: /água/i}, {attack: {lt: 50}}]}
db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 })












