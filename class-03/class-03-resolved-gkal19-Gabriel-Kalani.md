## MongoDB - Aula 03 - Exercício  
Autor: Gabriel Kalani

1. Liste todos Pokemons com a altura menor que 0.5;

```
	be-mean-pokemons> var query = {height : {$lt : 0.5}}
	be-mean-pokemons> query
	{
  		"height": {
    		"$lt": 0.5
  	}
}
	be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms

```

2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
	be-mean-pokemons> var query = {height : {$gte : 0.5}}
	be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
	be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56a90483529091c469c87feb"),
  "name": "Metagross",
  "description": "Esse cara é tão esperto quanto o mizeravi",
  "type": "esperto",
  "attack": 135,
  "defense": 130,
  "height": 1.6
}
{
  "_id": ObjectId("56a90674529091c469c87fec"),
  "name": "Pikachu",
  "description": "Um hamster/rato bem fofo e foda",
  "type": "raio",
  "attack": 58,
  "height": 0.9
}
{
  "_id": ObjectId("56a906fe529091c469c87fed"),
  "name": "Mewtwo",
  "description": "Uma \"cobaia de laboratório\" hahah ",
  "type": "fdp",
  "attack": 78,
  "height": 1
}
{
  "_id": ObjectId("56a907dd529091c469c87fee"),
  "name": "Suissa",
  "description": "Esse vai destruir o Capitalismo ehuehuehu",
  "type": "fodao",
  "attack": 100,
  "height": 2
}
{
  "_id": ObjectId("56a907fd529091c469c87fef"),
  "name": "Suissa",
  "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro e acabar com o capitalismo",
  "type": "fodao",
  "attack": 100,
  "height": 2
}
{
  "_id": ObjectId("56a908fc529091c469c87ff0"),
  "name": "Charmander",
  "description": "Pra quem procura fazer um churrasco no final de semana, o Charmander é uma boa opção",
  "type": "fogo",
  "attack": 46,
  "height": 0.9
}
	Fetched 6 record(s) in 11ms

```

3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
	be-mean-pokemons> var query = {$and:[{height:{$lte: 0.5}},{type:"grama"}]}
	be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms

```

4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
	be-mean-pokemons> var query = {$or:[{name:"Pikachu"},{attack:{$lte: 0.5}}]}
	be-mean-pokemons> db.pokemons.find(query)  
	{
  		"_id": ObjectId("56a90674529091c469c87fec"),
  		"name": "Pikachu",
  		"description": "Um hamster/rato bem fofo e foda",
  		"type": "raio",
  		"attack": 58,
  		"height": 0.9
	}
	Fetched 1 record(s) in 6ms
	
```

5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
	be-mean-pokemons> var query = {$and:[{attack:{$gte:48},height:{$lte:0.5}}]}
	be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms

```
