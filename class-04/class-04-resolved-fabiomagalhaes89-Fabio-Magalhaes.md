# MongoDB - Aula 04 - Exercício
autor: Fabio Magalhães

# 1 - Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Zigzagoon, Rapidash, Weedle e Charmeleon.

	> var query = {name: {$in: [/Zigzagoon/i, /Rapidash/i, /Weedle/i, /Charmeleon/i]}};
	
	> var attacks = ['investida','outro qualquer'];
	> var mod = {$pushAll: {moves: attacks}};
	> var options = {multi: true};
	
	> db.pokemons.update(query, mod, options);
	WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

	> db.pokemons.find(query);
	
	{ 
		"_id" : ObjectId("564a32925b2796ec7b69b932"), 
		"name" : "Rapidash", "description" : "Rápido pacaraio", 
		"type" : "fogo", 
		"attack" : 80, 
		"height" : 1.7, 
		"defense" : 40, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32db5b2796ec7b69b933"), 
		"name" : "Weedle", 
		"description" : "minhoca locura", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 1.6, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32f45b2796ec7b69b934"), 
		"name" : "Charmeleon", 
		"description" : "Tocha flamejante kk", 
		"type" : "fogo", 
		"attack" : 30, 
		"height" : 1.1, 
		"defense" : 30, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32495b2796ec7b69b931"), 
		"name" : "Zigzagoon", 
		"description" : "Descricao alterada para um pokemon malucao do gueto mermao! haha", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 25, 
		"moves" : [ "investida", "outro qualquer" ] 
	}

# 2 - Adicionar 1 movimento em todos os pokemons: desvio.
	> var query = {};
	> var mod = {$push: {moves: 'desvio'}};
	> var options = {multi: true};
	> db.pokemons.update(query, mod, options);
	WriteResult({ "nMatched" : 5, "nUpserted" : 0, "nModified" : 5 })

	> db.pokemons.find()
	{ 
		"_id" : ObjectId("564a32255b2796ec7b69b930"), 
		"name" : "Beedrill", 
		"description" : "Um pokemon ai", 
		"type" : "Loco", 
		"attack" : 70, 
		"height" : 1, 
		"defense" :	30, 
		"moves" : [ "desvio" ] 
	}
	{ 
		"_id" : ObjectId("564a32925b2796ec7b69b932"), 
		"name" : "Rapidash", 
		"description" : "Rápido pacaraio", 
		"type" : "fogo", 
		"attack" : 80, 
		"height" : 1.7, 
		"defense" : 40, 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}
	{ 
		"_id" : ObjectId("564a32db5b2796ec7b69b933"), 
		"name" : "Weedle", 
		"description" : "minhoca locura", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 1.6, 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}
	{ 
		"_id" : ObjectId("564a32f45b2796ec7b69b934"), 
		"name" : "Charmeleon", 
		"description" : "Tocha flamejante kk", 
		"type" : "fogo", 
		"attack" : 30, 
		"height" : 1.1, 
		"defense" : 30, 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}
	{ 
		"_id" : ObjectId("564a32495b2796ec7b69b931"), 
		"name" : "Zigzagoon", 
		"description" : "Descricao alterada para um pokemon malucao do gueto mermao! haha", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 25, 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}

# 3 - Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

	> var query = {name: /aindanaoexistemon/i};
	> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', attack: null, defense: null, height: null, description: 'Sem maiores informacoes'}};
	> var options = {upsert: true};
	> db.pokemons.update(query, mod, options);
	WriteResult({
	        "nMatched" : 0,
	        "nUpserted" : 1,
	        "nModified" : 0,
	        "_id" : ObjectId("565334b30d87b61835e3e788")
	})
	> db.pokemons.find(query);
	{ 
		"_id" : ObjectId("565334b30d87b61835e3e788"), 
		"name" : "AindaNaoExisteMon", 
		"attack" : null, 
		"defense" : null, 
		"height" : null, 
		"description" : "Sem maiores informacoes" 
	}

# 4 - Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

	> var query = {moves: {$in: ['investida']}};
	> db.pokemons.find(query);
	
	{ 
		"_id" : ObjectId("564a32925b2796ec7b69b932"), 
		"name" : "Rapidash", "description" : "Rápido pacaraio", 
		"type" : "fogo", 
		"attack" : 80, 
		"height" : 1.7, 
		"defense" : 40, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32db5b2796ec7b69b933"), 
		"name" : "Weedle", 
		"description" : "minhoca locura", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 1.6, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32f45b2796ec7b69b934"), 
		"name" : "Charmeleon", 
		"description" : "Tocha flamejante kk", 
		"type" : "fogo", 
		"attack" : 30, 
		"height" : 1.1, 
		"defense" : 30, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32495b2796ec7b69b931"), 
		"name" : "Zigzagoon", 
		"description" : "Descricao alterada para um pokemon malucao do gueto mermao! haha", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 25, 
		"moves" : [ "investida", "outro qualquer" ] 
	}

# 5 - Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
	> var query = {moves: {$in: ['investida', 'outro qualquer']}};
	> db.pokemons.find(query);

	{ 
		"_id" : ObjectId("564a32925b2796ec7b69b932"), 
		"name" : "Rapidash", "description" : "Rápido pacaraio", 
		"type" : "fogo", 
		"attack" : 80, 
		"height" : 1.7, 
		"defense" : 40, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32db5b2796ec7b69b933"), 
		"name" : "Weedle", 
		"description" : "minhoca locura", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 1.6, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32f45b2796ec7b69b934"), 
		"name" : "Charmeleon", 
		"description" : "Tocha flamejante kk", 
		"type" : "fogo", 
		"attack" : 30, 
		"height" : 1.1, 
		"defense" : 30, 
		"moves" : [ "investida", "outro qualquer" ] 
	}
	{ 
		"_id" : ObjectId("564a32495b2796ec7b69b931"), 
		"name" : "Zigzagoon", 
		"description" : "Descricao alterada para um pokemon malucao do gueto mermao! haha", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 25, 
		"moves" : [ "investida", "outro qualquer" ] 
	}

# 6 - Pesquisar todos os pokemons que não são do tipo fogo.
	> var query = {type: {$ne: 'fogo'}};
	> db.pokemons.find(query);
	{ 
		"_id" : ObjectId("5649f9fa5b2796ec7b69b92b"), 
		"name" : "Pikachu", 
		"description" : "Rato eletrico", 
		"type" : "eletric", 
		"attack" : 100, 
		"height" : 0.4, 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}
	{ 
		"_id" : ObjectId("5649fcef5b2796ec7b69b92c"), 
		"name" : "Bulbassauro", 
		"description" : "Chicote de trepadeira", 
		"type" : "grama", 
		"attack" : 49, 
		"height" : 0.4, 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}
	{ 
		"_id" : ObjectId("5649fe4f5b2796ec7b69b92e"), 
		"name" : "Squirtle", 
		"description" : "Ejeta agua que passarinho nao bebe", 
		"type" : "agua", 
		"attack" : 48, 
		"height" : 0.5, 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}
	{ 
		"_id" : ObjectId("564a13d35b2796ec7b69b92f"), 
		"name" : "Caterpie", 
		"description" : "Larva lutadora", 
		"type" : "inseto", 
		"attack" : 30, 
		"height" : 0.3, 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}
	{ 
		"_id" : ObjectId("56534751019a449eb538dd6c"), 
		"name" : "Beedrill", 
		"description" : "Um pokemon ai", 
		"type" : "Loco", 
		"attack" : 70, 
		"height" : 1, 
		"defense" : 30, 
		"moves" : [ "desvio" ] 
	}
	{ 
		"_id" : ObjectId("5653480971a99b6bfb731c6e"), 
		"name" : "AindaNaoExisteMon", 
		"attack" : null, 
		"defense" : null, 
		"height" : null, 
		"description" : "Sem maiores informacoes", 
		"moves" : [ "investida", "outro qualquer", "desvio" ] 
	}

# 7 - Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
	> var query = {$and: [{moves: 'investida'}, {defense: {$gt: 49}}]};
	> db.pokemons.find(query);

# 8 - Remova todos os pokemons do tipo água e com attack menor que 50.
	
	> var query = {$and: [{type: 'agua'}, {attack: {$lt: 50}}]};
	> db.pokemons.remove(query);
	WriteResult({ "nRemoved" : 1 })

# 9. Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.
	$ne - seleciona caso o valor seja diferente do especificado por exemplo:
	var query = {attack: {$ne: 30}};
	db.pokemons.find(query);	// esse comando irá retornar todos os pokemons que tiverem o ataque diferente de 30 ou seja, não igual a 30.

	$not - ele faz a negação do campo informado ou seja, trata como booleano por exemplo:
	var query = {attack: {$not: {$ne: 30}}};
	db.pokemons.find(query);	//ira retornar todos os pokemons que tiverem o ataque igual a 30 pois foi feita uma negação da condição anterior. 