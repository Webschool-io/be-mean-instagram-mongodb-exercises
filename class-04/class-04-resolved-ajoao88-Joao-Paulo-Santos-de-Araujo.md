#MongoDB - Aula 04 - Exercícios
autor: João Paulo Santos de Araújo

##1. **Adicionar** 2 ataques ao mesmo tempo para mais de um pokemon

	```
	var query = {name: {$in: [/pikachu/i,/heatran/i]}}
	db.pokemons.find(query);
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f78"), 
		"name" : "heatran", 
		"description" : "bicho doido", 
		"type" : "Lava Dome", 
		"attack" : 500, 
		"defense" : 500, 
		"height" : 1.7, 
		"moves" : [ "Investida", "Picada de Tanajura" ] 
	}
	{ 
		"_id" : ObjectId("5643f5ac8a3351185ddd5461"), 
		"name" : "Pikachu", 
		"description" : "Rato elétrico", 
		"type" : "eletric", 
		"attack" : 1500, 
		"height" : 0.4, 
		"moves" : [ "Investida", "Raio do trovão" ] 
	};

	```

	```
	var mod = {$pushAll: {moves: ['Ataque1','Ataque2']}};
	var options = {multi: true};
	db.pokemons.update(query,mod,options);
	```

	```
	var campos = {name: 1,moves: 1}
	db.pokemons.find(query,campos);
	{ 
		"_id" : ObjectId("5643f5ac8a3351185ddd5461"), 
		"name" : "Pikachu", 
		"moves" : [ "Investida", "Raio do trovão", "Ataque1", "Ataque2" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f78"), 
		"name" : "heatran", 
		"moves" : [ "Investida", "Picada de Tanajura", "Ataque1", "Ataque2"]
	}
	```

##2. **Adicionar** 1 Movimento em todos os pokemons: `desvio`.

	```
	var query = {};
	var mod = {$push: {moves: 'Desvio'}};
	var options = {multi: true};
	db.pokemons.update(query,mod,options);
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f79"), 
		"name" : "luxray", 
		"moves" : [ "Investida", "Raio X", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7a"), 
		"name" : "bouffalant", 
		"moves" : [ "Investida", "Fala da Cindel", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7b"), 
		"name" : "Mega mewtwo Y", 
		"moves" : [ "Investida", "Ataque Mewthree", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7c"), 
		"name" : "Armaldo", 
		"moves" : [ "Investida", "Armadilha do Armaldo", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5643f5ac8a3351185ddd5461"), 
		"name" : "Pikachu", 
		"moves" : [ "Investida", "Raio do trovão", "Ataque1", "Ataque2", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5643f6e88a3351185ddd5462"), 
		"name" : "Testemon", 
		"moves" : [ "Investida", "Ataque1", "Ataque2", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("564a8acc63eb284f0c5a3637"), 
		"name" : "Testemon", 
		"moves" : [ "Investida", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("564f017c31f686fc0a142401"),
		 "name" : "teste", 
		 "moves" : [ "mov1", "mov2", "Desvio" ] 
		}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f78"), 
		"name" : "heatran", 
		"moves" : [ "Investida", "Picada de Tanajura","Ataque1", "Ataque2", "Desvio" ] 
	}
	```

##3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: `Sem maiores informações`.

	```
	var mod = {$set: {name: 'naoExiste'},$setOnInsert: {description: 'Sem Maiores Informações',type: null,attack: null, defense: null, height: null}};
	var options = { "upsert" : true };
	var query = {name: /existe/i};
	db.pokemons.update(query,mod,options);
	WriteResult({
	        "nMatched" : 0,
	        "nUpserted" : 1,
	        "nModified" : 0,
	        "_id" : ObjectId("564f16aa80ac1ec50f141c5e")
	});
	var query = {name: /naoExiste/i};
	db.pokemons.find(query)
	{ "_id" : ObjectId("564f16aa80ac1ec50f141c5e"), "name" : "naoExiste", "description" : "Sem Maiores Informações", "type" : null, "attack" : null, "defense" : null, "height" : null }
	```

##4. Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito

	```
	var query = {moves: {$in: [/investida/i,/desvio/i]}};
	db.pokemons.find(query);
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f79"), 
		"name" : "luxray", 
		"moves" : [ "Investida", "Raio X", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7a"), 
		"name" : "bouffalant", 
		"moves" : [ "Investida", "Fala da Cindel", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7b"), 
		"name" : "Mega mewtwo Y", 
		"moves" : [ "Investida", "Ataque Mewthree", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7c"), 
		"name" : "Armaldo", 
		"moves" : [ "Investida", "Armadilha do Armaldo", "Desvio" ]
	}
	{ 
		"_id" : ObjectId("5643f5ac8a3351185ddd5461"), 
		"name" : "Pikachu", 
		"moves" : [ "Investida", "Raio do trovão", "Ataque1", "Ataque2", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5643f6e88a3351185ddd5462"), 
		"name" : "Testemon", 
		"moves" : [ "Investida", "Ataque1", "Ataque2", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("564a8acc63eb284f0c5a3637"), 
		"name" : "Testemon", 
		"moves" : [ "Investida", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("564f017c31f686fc0a142401"), 
		"name" : "teste", 
		"moves" : [ "mov1", "mov2", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f78"), 
		"name" : "heatran", 
		"moves" : [ "Investida", "Picada de Tanajura", "Desvio", "Ataque1", "Ataque2" ] 
	}
	```

##5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

	```
	var query = {moves: {$all: [/grito da cindel/i,/investida/i]}};
	var campos = {name: 1,moves: 1};
	db.pokemons.find(query,campos);
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7a"), 
		"name" : "bouffalant", "moves" : [ "Investida", "Grito da Cindel", "Desvio" ] 
	}
	```

##6. Pesquisar **todos** os pokemons que não são do tipo `eletric`.

	```
	var query = {type: {$not: /eletric/i}};
	var campos = {name: 1, type: 1};
	db.pokemons.find(query,campos);
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f79"), 
		"name" : "luxray", 
		"type" : "besta" 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7a"), 
		"name" : "bouffalant", 
		"type" : "Bufalis" 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7b"), 
		"name" : "Mega mewtwo Y", 
		"type" : "Psychic" 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7c"), 
		"name" : "Armaldo", 
		"type" : "Rock" 
	}
	{ 
		"_id" : ObjectId("5643f6e88a3351185ddd5462"), 
		"name" : "Testemon" 
	}
	{ 
		"_id" : ObjectId("564a8acc63eb284f0c5a3637"), 
		"name" : "Testemon" 
	}
	{ 
		"_id" : ObjectId("564f017c31f686fc0a142401"), 
		"name" : "teste", 
		"type" : "tipo teste" 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f78"), 
		"name" : "heatran", 
		"type" : "Lava Dome" 
	}
	{ 
		"_id" : ObjectId("564f16aa80ac1ec50f141c5e"), 
		"name" : "naoExiste", 
		"type" : null 
	}
	```

##7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

	```
	var query = {$and: [{moves: /investida/i},{defense: {$gte: 500}}]};
	var campos = {name: 1, moves: 1, defense: 1};
	db.pokemons.find(query,campos);
	{ 
		"_id" : ObjectId("5643f6e88a3351185ddd5462"), 
		"name" : "Testemon", 
		"defense" : 8000, 
		"moves" : [ "Investida", "Ataque1", "Ataque2", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("564a8acc63eb284f0c5a3637"), 
		"name" : "Testemon", 
		"defense" : 8000, 
		"moves" : [ "Investida", "Desvio" ] 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f78"), 
		"name" : "heatran", 
		"defense" : 500, 
		"moves" : [ "Investida", "Picada de Tanajura", "Desvio", "Ataque1", "Ataque2" ] 
	}


	```

##8. Remova **todos** os pokemons de um determinado tipo e com attack menor que 600.

	```
	var query = {$and: [{type: /tipo test/i},{attack: {$lt: 600}}]};
	var campos = {name: 1, type: 1, attack: 1};
	db.pokemons.find(query,campos);
	{ "_id" : ObjectId("564f017c31f686fc0a142401"), "name" : "teste", "type" : "tipo teste", "attack" : 500 };
	db.pokemons.remove(query);
	WriteResult({ "nRemoved" : 1 });
	db.pokemons.find(query,campos);

	```