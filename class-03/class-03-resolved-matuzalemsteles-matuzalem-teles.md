# MongoDB - Aula 03 - Exercício
autor: Matuzalém Teles

## Liste todos Pokemons com a altura **menor que** 0.5;
	> var query = {height:{$lte:0.5}}
	> query
	{ "height" : { "$lte" : 0.5 } }
	> db.pokemons.find(query)
	{ "_id" : ObjectId("5643456be80d6742ece646ae"), "name" : "Pikachu", "description" : "Ele é bixão doido e elétrico", "type" : "electric", "attack" : 100, "height" : 0.4 }
	{ "_id" : ObjectId("56434695e80d6742ece646af"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4}
	{ "_id" : ObjectId("56434799e80d6742ece646b1"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
	> var query = {height:{$gte:0.5}}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("56434762e80d6742ece646b0"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52,"height" : 0.6 }
	{ "_id" : ObjectId("56434799e80d6742ece646b1"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
	{ "_id" : ObjectId("56434fd51b65a2def9e9725a"), "name" : "Charmeleon", "description" : "Um mini dragão com rabo pegando fogo", "attack" : 80, "defense" : 65, "height" : 11 }
	{ "_id" : ObjectId("56434fdc1b65a2def9e9725b"), "name" : "Pikachu", "description" : "Ele é bixão doido e elétrico", "attack" : 50, "defense" : 50, "height" : 4}
	{ "_id" : ObjectId("56434fe41b65a2def9e9725c"), "name" : "Ivysaur ", "description" : "Com dente e uma planta loca na costa", "attack" : 80, "defense" : 80, "height" : 10 }
	{ "_id" : ObjectId("56434fed1b65a2def9e9725d"), "name" : "Blastoise ", "description" : "Tartaruga com vida loka", "attack" : 85, "defense" : 105, "height" : 16}
	{ "_id" : ObjectId("56434ff31b65a2def9e9725e"), "name" : "Rattata", "description" : "Rato vida loka", "attack" : 25, "defense" : 35, "height" : 3 }
	
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
	> var query = ( { $or: [ { height: { $lt: 0.5 } }, { type: 'grass' } ] } )
	> db.pokemons.find(query)
	{ "_id" : ObjectId("5643456be80d6742ece646ae"), "name" : "Pikachu", "description" : "Ele é bixão doido e elétrico", "type" : "electric", "attack" : 100, "height" : 0.4 }
	{ "_id" : ObjectId("56434695e80d6742ece646af"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4}

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
	> var query = { $or: [ { name: 'Pikachu' }, { attack: { $lte: 0.5 } } ] }
	> db.pokemons.find(query)
	{ "_id" : ObjectId("5643456be80d6742ece646ae"), "name" : "Pikachu", "description" : "Ele é bixão doido e elétrico", "type" : "electric", "attack" : 100, "height" : 0.4 }
	{ "_id" : ObjectId("56434fdc1b65a2def9e9725b"), "name" : "Pikachu", "description" : "Ele é bixão doido e elétrico", "attack" : 50, "defense" : 50, "height" : 4}

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
	> var query = { $and: [ { attack: { $gte:48 } }, { height: { $lte: 0.5 } } ] }
	> db.pokemons.find(query)
	{ "_id" : ObjectId("5643456be80d6742ece646ae"), "name" : "Pikachu", "description" : "Ele é bixão doido e elétrico", "type" : "electric", "attack" : 100, "height" : 0.4 }
	{ "_id" : ObjectId("56434695e80d6742ece646af"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4}
	{ "_id" : ObjectId("56434799e80d6742ece646b1"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }