# MongoDB - Aula 02 - Exercício
	autor: Valdir Pereira

#1. Crie uma database chamada be-mean-pokemons;
	> use be-mean-pokemons
	switched to db be-mean-pokemons


#2. Liste quais databases você possui nesse servidor;
#Antes de inserir os pokemons no novo database:
	> show dbs
	be-mean            0.078GB
	be-mean-instagram  0.078GB
	local              0.078GB


#3. Liste quais coleções você possui nessa database;
	> show collections


#4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;
	
	> var pokemon = [
	... {
	... 'name': 'chikorita',
	... 'description': 'Pedaço de folha viva',
	... attack: 100,
	... defense: 50,
	... height: 20
	... },
	... {
	... 'name': 'Growlithe ',
	... 'description': 'lobo sentimental',
	... attack: 40,
	... defense: 20
	... },
	... {
	... 'name': 'Magnemite',
	... 'description': 'Imã voador em formato de olho',
	... attack: 20,
	... defense: 30,
	... height: 0.3
	... },
	... {
	... 'name': 'Onix',
	... 'description': 'Minhoca pedrificada',
	... attack: 20,
	... defense: 70,
	... height: 8.8
	... },
	... {
	... 'name': 'Horsea',
	... 'description': 'cavalo marinho bebe',
	... attack: 20,
	... defense: 30,
	... height: 0.4
	... }
	... ]
	> db
	be-mean-pokemons
	> db.pokemons.insert(pokemon)
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
	> show collections
	pokemons
	system.indexes


#5. Liste os pokemons existentes na sua coleção;

> db.pokemons.find().pretty()
{
        "_id" : ObjectId("5644621bf90ae9153747a911"),
        "name" : "chikorita",
        "description" : "Pedaço de folha",
        "attack" : 100,
        "defense" : 50,
        "height" : 20
}
{
        "_id" : ObjectId("5644621bf90ae9153747a912"),
        "name" : "Growlithe ",
        "description" : "lobo sentimental",
        "attack" : 40,
        "defense" : 20
}
{
        "_id" : ObjectId("5644621bf90ae9153747a913"),
        "name" : "Magnemite",
        "description" : "Imã voador em formato de olho",
        "attack" : 20,
        "defense" : 30,
        "height" : 0.3
}
{
        "_id" : ObjectId("5644621bf90ae9153747a914"),
        "name" : "Onix",
        "description" : "Minhoca pedrificada",
        "attack" : 20,
        "defense" : 70,
        "height" : 8.8
}
{
        "_id" : ObjectId("5644621bf90ae9153747a915"),
        "name" : "Horsea",
        "description" : "cavalo marinho bebe",
        "attack" : 20,
        "defense" : 30,
        "height" : 0.4
}


#6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

	> var query = {name: 'Onix'}
	> query
	{ "name" : "Onix" }
	> var poke = db.pokemons.findOne(query)
	> poke
	{
	        "_id" : ObjectId("5644621bf90ae9153747a914"),
	        "name" : "Onix",
	        "description" : "Minhoca pedrificada",
	        "attack" : 20,
	        "defense" : 70,
	        "height" : 8.8
	}


#7. Modifique sua `description` e salvê-o

	> poke.description
	Minhoca pedrificada
	> poke.description = 'Michoca marombeira pedrificada'
	Michoca marombeira pedrificada
	> db.pokemons.save(poke)
	WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })