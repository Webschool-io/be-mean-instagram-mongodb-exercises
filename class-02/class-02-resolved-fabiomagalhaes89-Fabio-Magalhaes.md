
1. Criar uma database chamada be-mean-pokemons;

	> use be-mean-pokemons
	switched to db be-mean-pokemons

2. Liste quais databases você possui nesse servidor;

	> show databases
	be-mean            0.078GB
	be-mean-instagram  0.078GB
	local              0.078GB

3. Insira pelo menos 5 pokemons a sua escolha utilizando o mesmo padrao de campos, name, description, attack, defense e height;

	> var pokemon = {'name': 'Beedrill', 'description': 'Um pokemon ai', 'type':'Loco', attack:70, height: 1, defense: 30};
	> db.meuspokemons.insert(pokemon);
	WriteResult({ "nInserted" : 1 })

	> var pokemon = {'name': 'Zigzagoon', 'description': 'Inquieto, vagueia em todos os lugares, em todos os momentos', 'type':'Normal', attack:45, height: 0.4, defense: 25};
	> db.pokemons.insert(pokemon);
	WriteResult({ "nInserted" : 1 })

	> var pokemon = {'name': 'Rapidash', 'description': 'Rápido pacaraio', 'type':'fogo', attack:80, height: 1.7, defense: 40};
	> db.pokemons.insert(pokemon);
	WriteResult({ "nInserted" : 1 })

	>  var pokemon = {'name': 'Weedle', 'description': 'minhoca locura', 'type':'Normal', attack:45, height: 0.4, defense: 1.6};
	> db.pokemons.insert(pokemon);
	WriteResult({ "nInserted" : 1 })

	> var pokemon = {'name': 'Charmeleon', 'description': 'Tocha flamejante kk', 'type':'fogo', attack:30, height: 1.1, defense: 30};
	> db.pokemons.insert(pokemon);
	WriteResult({ "nInserted" : 1 })

4. Liste os pokemons existentes na sua coleção;
	
	> db.pokemons.find()
	{ 	
		"_id" : ObjectId("564a32255b2796ec7b69b930"), 
		"name" : "Beedrill", 
		"description" : "Um pokemon ai", 
		"type" : "Loco", 
		"attack" : 70, 
		"height" : 1, 
		"defense" : 30 
	}
	{ 
		"_id" : ObjectId("564a32495b2796ec7b69b931"), 
		"name" : "Zigzagoon", 
		"description" : "Inquieto, vagueia em todos os lugares, em todos os momentos", 
		"type" : "Normal", "attack" : 45, 
		"height" : 0.4, 
		"defense" : 25 
	}
	{ 
		"_id" : ObjectId("564a32925b2796ec7b69b932"), 
		"name" : "Rapidash", 
		"description" : "Rápido pacaraio", 
		"type" : "fogo", 
		"attack" : 80, 
		"height" : 1.7, 
		"defense" : 40 
	}
	{ 
		"_id" : ObjectId("564a32db5b2796ec7b69b933"), 
		"name" : "Weedle", 
		"description" : "minhoca locura", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 1.6 
	}
	{ 
		"_id" : ObjectId("564a32f45b2796ec7b69b934"), 
		"name" : "Charmeleon", 
		"description" : "Tocha flamejante kk", 
		"type" : "fogo", 
		"attack" : 30, 
		"height" : 1.1, 
		"defense" : 30 
	}

5. Busque o pokemon a sua escolha pelo nome e armazene-o em uma variavel chamada poke;

	> var query = {'name':'Zigzagoon'};
	> var poke = db.pokemons.findOne(query);
	> poke
	{
	        "_id" : ObjectId("564a32495b2796ec7b69b931"),
	        "name" : "Zigzagoon",
	        "description" : "Inquieto, vagueia em todos os lugares, em todos os momentos",
	        "type" : "Normal",
	        "attack" : 45,
	        "height" : 0.4,
	        "defense" : 25
	}

6. modifique sua description e salve-o

	> poke.description = 'Descricao alterada para um pokemon malucao do gueto mermao! haha';
	Descricao alterada para um pokemon malucao do gueto mermao! haha
	> poke
	{
        "_id" : ObjectId("564a32495b2796ec7b69b931"),
        "name" : "Zigzagoon",
        "description" : "Descricao alterada para um pokemon malucao do gueto mermao! haha",
        "type" : "Normal",
        "attack" : 45,
        "height" : 0.4,
        "defense" : 25
	}
	> db.pokemons.save(poke);
	WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })