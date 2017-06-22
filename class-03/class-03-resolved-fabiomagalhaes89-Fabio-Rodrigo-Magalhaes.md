# MongoDB - Aula 03 - Exercício
autor: Fabio Rodrigo Magalhães
## 1. Liste todos Pokemons com a altura menor que 0.5;
	> var query = {height: {$lt: 0.5}};
	> db.pokemons.find(query);
	{ 
		"_id" : ObjectId("564a32495b2796ec7b69b931"), 
		"name" : "Zigzagoon", 
		"description" : "Descricao alterada para um pokemon malucao do gueto mermao! haha", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 25 
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

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;
	> var query = {height: {$gte: 0.5}};
	> db.pokemons.find(query);
	{ 
		"_id" : ObjectId("564a32255b2796ec7b69b930"), 
		"name" : "Beedrill", 
		"description" : "Um pokemon ai", 
		"type" : "Loco", 
		"attack" : 70, 
		"height" : 1, 
		"defense" :	30 
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
		"_id" : ObjectId("564a32f45b2796ec7b69b934"), 
		"name" : "Charmeleon", 
		"description" : "Tocha flamejante kk", 
		"type" : "fogo", 
		"attack" : 30, 
		"height" : 1.1, 
		"defense" : 30 
	}

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
	> var query = {$and [{height: {$lte: 0.5}},{type: "Normal"}]};
	> db.pokemons.find(query);
	{ 
		"_id" : ObjectId("564a32495b2796ec7b69b931"), 
		"name" : "Zigzagoon", 
		"description" : "Descricao alterada para um pokemon malucao do gueto mermao! haha", 
		"type" : "Normal",
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 25 
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

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
	> var query = {$or: [{name: "Charmeleon"}, {attack: {$lte: 30}}]};
	> db.pokemons.find(query);
	{ 
		"_id" : ObjectId("564a32f45b2796ec7b69b934"), 
		"name" : "Charmeleon", 
		"description" : "Tocha flamejante kk", 
		"type" : "fogo", 
		"attack" : 30, 
		"height" : 1.1, 
		"defense" : 30 
	}

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;
	> var query = {$and: [{attack: {$gte: 45}}, {height: {$lte: 0.5}}]};
	> db.pokemons.find(query);
	{ 
		"_id" : ObjectId("564a32495b2796ec7b69b931"), 
		"name" : "Zigzagoon", 
		"description" : "Descricao alterada para um pokemon malucao do gueto mermao! haha", 
		"type" : "Normal", 
		"attack" : 45, 
		"height" : 0.4, 
		"defense" : 25 
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
