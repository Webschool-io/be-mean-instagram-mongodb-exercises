#MongoDB - Aula 02 - Exercício
Autor: Henrique Nascimento

#Criar database chamada be-mean-pokemons
    
    use be-mean-pokemons
    switched to db be-mean-pokemons
    
#Listagem de todas as dbs

    
    show dbs
    be-mean           → 0.005GB
    be-mean-instagram → 0.005GB
    local             → 0.000GB
    

#Listagem das collections

    show collections

#Criar pelo menos 5 pokemons
    
    var pokedex = [
	{'name':'Blastoise', 'description':'Pokemon aguatico evolução Nº 009 do Squirtle', 'type':'Water', 'attack':40, 'height':1.6, 'defense': 40},
	{'name':'Batterfree', 'description':'Pokemon voador', 'type':'Bug', 'attack':20, 'height':1.1, 'defense': 20},
	{'name':'Abra', 'description':'Pokemon que usa a mente', 'type':'Psychic', 'attack':10, 'height':0.9, 'defense':10},
	{'name':'Aipom', 'description':'Pokemon macaco', 'type':'Normal', 'attack':40, 'height': 0.8, 'defense': 30},
	{'name':'Absol', 'description':'Pokemon Dark', 'type':'Dark', 'attack':70, 'height':1.2, 'defense': 30}
	]

    henrique-nasc(mongod-3.2.11) be-mean-pokemons> db.pokemon.insert(pokedex)
    Inserted 1 record(s) in 341ms
    BulkWriteResult({
    "writeErrors": [ ],
    "writeConcernErrors": [ ],
    "nInserted": 5,
    "nUpserted": 0,
    "nMatched": 0,
    "nModified": 0,
    "nRemoved": 0,
    "upserted": [ ]
    })

    
#Listando os pokemons

    
    be-mean-pokemons> db.pokemon.find()
    {
    "_id": ObjectId("58627adeaa3029422af2f9fb"),
    "name": "Blastoise",
    "description": "Pokemon aguatico evolução Nº 009 do Squirtle",
    "type": "Water",
    "attack": 40,
    "height": 1.6,
    "defense": 40
    }
    {
    "_id": ObjectId("58627adeaa3029422af2f9fc"),
    "name": "Batterfree",
    "description": "Pokemon voador",
    "type": "Bug",
    "attack": 20,
    "height": 1.1,
    "defense": 20
    }
    {
    "_id": ObjectId("58627adeaa3029422af2f9fd"),
    "name": "Abra",
    "description": "Pokemon que usa a mente",
    "type": "Psychic",
    "attack": 10,
    "height": 0.9,
    "defense": 10
    }
    {
    "_id": ObjectId("58627adeaa3029422af2f9fe"),
    "name": "Aipom",
    "description": "Pokemon macaco",
    "type": "Normal",
    "attack": 40,
    "height": 0.8,
    "defense": 30
    }
    {
    "_id": ObjectId("58627adeaa3029422af2f9ff"),
    "name": "Absol",
    "description": "Pokemon Dark",
    "type": "Dark",
    "attack": 70,
    "height": 1.2,
    "defense": 30
    }
    Fetched 5 record(s) in 1ms
   
#Buscando Pokemon pelo nome

    be-mean-pokemons> var busca = {name:'Abra'}
    be-mean-pokemons> var poke = db.pokemon.findOne(busca)
    be-mean-pokemons> poke
    {
    "_id": ObjectId("58627adeaa3029422af2f9fd"),
    "name": "Abra",
    "description": "Pokemon que usa a mente",
    "type": "Psychic",
    "attack": 10,
    "height": 0.9,
    "defense": 10
    }


#Alterando a descrição do pokemon escolhido pelo nome

    be-mean-pokemons> poke.description = 'Pokemon que literalmente usa a cabeça'
    Pokemon que literalmente usa a cabeça

    be-mean-pokemons> db.pokemon.save(poke)

    be-mean-pokemons> poke
    {
    "_id": ObjectId("58627adeaa3029422af2f9fd"),
    "name": "Abra",
    "description": "Pokemon que literalmente usa a cabeça",
    "type": "Psychic",
    "attack": 10,
    "height": 0.9,
    "defense": 10
    }

    
