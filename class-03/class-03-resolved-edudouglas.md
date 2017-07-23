# MongoDB - Aula 03 - Exercício
autor: Eduardo Douglas da Silva

# Liste todos Pokemons com a altura menor que 0.5; (passo 1)
> mongo be-mean-pokemons
> var query = {height: {$lt:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56474a15949f581ad1921ff3"), "name" : "Beedrill", "description" : "Tipo Inseto", "atack" : 60, "defense" : 50, "height" : 0.3 }
{ "_id" : ObjectId("56474a15949f581ad1921ff4"), "name" : "Pidgey", "description" : "Tipo Passaro", "atack" : 60, "defense" : 50, "height" : 0.4 }

# Liste todos Pokemons com a altura maior ou igual que 0.5; (passo 2)
> var query = {height: {$gte:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564747ba8990240dfd5b1a59"), "name" : "Zapdos", "description" : "Tipo Elétrico", "atack" : 60, "defense" : 50, "height" : 5.3 }
{ "_id" : ObjectId("564747ba8990240dfd5b1a5a"), "name" : "Articuno", "description" : "Tipo Gelo", "atack" : 50, "defense" : 50, "height" : 4.1 }
{ "_id" : ObjectId("564747ba8990240dfd5b1a5b"), "name" : "Charizard", "description" : "Tipo Dragão Voador", "atack" : 47, "defense" : 49, "height" : 90.5 }
{ "_id" : ObjectId("564747ba8990240dfd5b1a5c"), "name" : "Bulbasaur", "description" : "Tipo Planta", "atack" : 25, "defense" : 25, "height" : 6.9 }
{ "_id" : ObjectId("564747ba8990240dfd5b1a5d"), "name" : "Tauros", "description" : "Tipo Touro Bravo", "atack" : 56, "defense" : 40, "height" : 88.4 }

# Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama; (passo 3)
> var query = {$and: [{ height:{ $lte:0.5 } } , { type: "grama" } ]}
> db.pokemons.find(query)

// Alterei o parametro para retornar dados na minha consulta

> var query = {$and: [ {height:{$lte:0.5}} , {type:'mouse'} ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("56474b68949f581ad1921ff5"), "name" : "Rattata", "description" : "Tipo Rato", "type" : "mouse", "atack" : 60, "defense" : 50, "height" : 0.3 }
{ "_id" : ObjectId("56474b68949f581ad1921ff6"), "name" : "Raticate", "description" : "Tipo Rato", "type" : "mouse", "atack" : 60, "defense" : 50, "height" : 0.4 }

# Listando os pokemons com nome 'Rattata' OU attack menor ou igual que 0.5 (passo 4)
> var query = {$or: [ {name:'Rattata'}, {height:{$lte:0.5}} ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("56474a15949f581ad1921ff3"), "name" : "Beedrill", "description" : "Tipo Inseto", "atack" : 60, "defense" : 50, "height" : 0.3 }
{ "_id" : ObjectId("56474a15949f581ad1921ff4"), "name" : "Pidgey", "description" : "Tipo Passaro", "atack" : 60, "defense" : 50, "height" : 0.4 }
{ "_id" : ObjectId("56474b68949f581ad1921ff5"), "name" : "Rattata", "description" : "Tipo Rato", "type" : "mouse", "atack" : 60, "defense" : 50, "height" : 0.3 }
{ "_id" : ObjectId("56474b68949f581ad1921ff6"), "name" : "Raticate", "description" : "Tipo Rato", "type" : "mouse", "atack" : 60, "defense" : 50, "height" : 0.4 }

# Listando pokemons com attack MAIOR OU IGUAL QUE 48 E height menor ou igual que 0.5 (passo 5)
> var query = {$and: [ {attack:{$gte:48}} , {height:{$lte:0.5}} ] }
> db.pokemons.find(query)

> var query = {$and: [ {atack:{$gte:60}} , {height:{$lte:0.4}} ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("56474a15949f581ad1921ff3"), "name" : "Beedrill", "description" : "Tipo Inseto", "atack" : 60, "defense" : 50, "height" : 0.3 }
{ "_id" : ObjectId("56474a15949f581ad1921ff4"), "name" : "Pidgey", "description" : "Tipo Passaro", "atack" : 60, "defense" : 50, "height" : 0.4 }
{ "_id" : ObjectId("56474b68949f581ad1921ff5"), "name" : "Rattata", "description" : "Tipo Rato", "type" : "mouse", "atack" : 60, "defense" : 50, "height" : 0.3 }
{ "_id" : ObjectId("56474b68949f581ad1921ff6"), "name" : "Raticate", "description" : "Tipo Rato", "type" : "mouse", "atack" : 60, "defense" : 50, "height" : 0.4 }






