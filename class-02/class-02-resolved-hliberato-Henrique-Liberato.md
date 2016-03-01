MongoDB - Aula 02 - Exercício
autor: Henrique Liberato

## 1
henrique(mongod-3.2.3) test> db.createCollection("be-mean-pokemon")
henrique(mongod-3.2.3) test> use be-mean-pokemon
switched to db be-mean-pokemon

## 2
henrique(mongod-3.2.3) be-mean-pokemon> show dbs

## 3
henrique(mongod-3.2.3) be-mean-pokemon> show collections

## 4
var pokemon = {
	name:'Pikachu',
	description:'Rato elétrico',
	type:'Eletric',
	attack:55,
	defense:41,
	height:0.4
} ;
db.pokemons.insert(pokemon);

pokemon = {
	name:'Bulbassauro',
	description:'Coma seus vegetais, filho',
	type:'Salada',
	attack:49,
	defense:74,
	height:0.4
};
db.pokemons.insert(pokemon);

pokemon = {
	name:'Charmander',
	description:'Pegam só pra ter o charizard',
	type:'fogo',
	attack:52,
	defense:42,
	height:0.6
};
db.pokemons.insert(pokemon);

pokemon = {
	name:'Squirtle',
	description:'Jabuti brigadista',
	type:'Eletric',
	attack:48,
	defense:30,
	height:0.5
};
db.pokemons.insert(pokemon);

pokemon = {
	name:'Mew',
	description:'Gatinha manhosa',
	type:'Psiquico',
	attack:8000,
	defense:8000,
	height:0.3
};
db.pokemons.insert(pokemon);

## 5
henrique(mongod-3.2.3) be-mean-pokemon> db.pokemons.find()

## 6
henrique(mongod-3.2.3) be-mean-pokemon> var query = {name: 'Pikachu'}
henrique(mongod-3.2.3) be-mean-pokemon> var poke = db.pokemons.find(query)

henrique(mongod-3.2.3) be-mean-pokemon> poke
{
  "_id": ObjectId("56d5d625e9b6be167932defa"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "Eletric",
  "attack": 55,
  "defense": 41,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

## 7
henrique(mongod-3.2.3) be-mean-pokemon> var query = {name: 'Pikachu'}
henrique(mongod-3.2.3) be-mean-pokemon> var poke = db.pokemons.findOne(query)
henrique(mongod-3.2.3) be-mean-pokemon> poke.defense = 10
henrique(mongod-3.2.3) be-mean-pokemon> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})