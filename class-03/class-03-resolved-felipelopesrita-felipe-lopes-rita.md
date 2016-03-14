# MongoDB - Aula 03 - Exercício
autor: Felipe José Lopes Rita

## Liste todos Pokemons com a altura **menor que** 0.5;
```
StarKiller(mongod-3.2.0) be-mean-pokemons> var query = {height:{$lt: 0.5}}
StarKiller(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b4237765cd05bf6bff3323"),
  "name": "Minun",
  "description": "Coelho elétrico que parece mas não tem nada a ver com o pikachu",
  "attack": 40,
  "defense": 50,
  "height": 0.4
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3325"),
  "name": "Pidgey",
  "description": "Pomba comum de Sampa, só que não caga em você (acho)",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
StarKiller(mongod-3.2.0) be-mean-pokemons> var query = {height:{$gte: 0.5}}
StarKiller(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b4237765cd05bf6bff3322"),
  "name": "Cyndaquil",
  "description": "Tem fogo nas costas e é fofo pra caralho",
  "attack": 52,
  "defense": 43,
  "height": 0.5,
  "descricao": "Sempre escolhia ele quando jogava pokemon Gold & Silver"
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3324"),
  "name": "Charizard",
  "description": "Pokemon mais pica das galáxias",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3326"),
  "name": "Zorua",
  "description": "Raposa preta (deve ser do capeta) foda e fofa",
  "attack": 65,
  "defense": 40,
  "height": 0.7
}
Fetched 3 record(s) in 4ms
StarKiller(mongod-3.2.0) be-mean-pokemons>
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
StarKiller(mongod-3.2.0) be-mean-pokemons> var query = { $and:[ {type:'grass'}, {height: {$lte: 0.5} } ] }
StarKiller(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
StarKiller(mongod-3.2.0) be-mean-pokemons> var query = { $or:[ {name:'Pikachu'}, {attack: {$lte: 0.5}} ] }
StarKiller(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b4dc2c6590f68f8a2b12a8"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
StarKiller(mongod-3.2.0) be-mean-pokemons> var query = { $and: [ {attack:{$gte:48}}, {height:{$lte:0.5}} ] }
StarKiller(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b4237765cd05bf6bff3322"),
  "name": "Cyndaquil",
  "description": "Tem fogo nas costas e é fofo pra caralho",
  "attack": 52,
  "defense": 43,
  "height": 0.5,
  "descricao": "Sempre escolhia ele quando jogava pokemon Gold & Silver"
}
{
  "_id": ObjectId("56b4dc2c6590f68f8a2b12a8"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}
```