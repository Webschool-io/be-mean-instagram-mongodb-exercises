# MongoDB - Aula 02 - Exercício
autor: Luiz Fernando Cieslak

## 1. Criar DB be-mean-pokemons

```
luizcieslak-N150SD-N155SD(mongod-2.6.10) pokemon> use be-mean-pokemons
switched to db be-mean-pokemons
```

## 2. Mostrar os DBs existentes
```
luizcieslak-N150SD-N155SD(mongod-2.6.10) be-mean-pokemons> show dbs
admin             → (empty)
algdock           → 0.078GB
be-mean           → 0.078GB
be-mean-instagram → (empty)
local             → 0.078GB
pokemon           → 0.078GB
pokemons          → 0.078GB
test              → 0.078GB
```

## 3. Mostrar as collections existentes dentro do db

```
luizcieslak-N150SD-N155SD(mongod-2.6.10) be-mean-pokemons> show collections
(vazio)
```

## 4. Inserir 5 pokemons
```
db.pokemons.insert({
  "name": "Pikachu",
  "description": "shazam carai",
  "type": "electric",
  "attack": 55,
  "defense": 20,
  "height": 0.4
})
```
```
Inserted 1 record(s) in 293ms
WriteResult({
  "nInserted": 1
})
```
```
db.pokemons.insert({
  "name": "Oddish",
  "description": "planta verde mt louca",
  "type": "grama",
  "attack": 60,
  "defense": 30,
  "height": 0.3
})
```
```
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```
```
db.pokemons.insert({
  "name": "Starmie",
  "description": "estrela de 8 pontas roxa que solta agua",
  "type": "agua",
  "attack": 80,
  "defense": 50,
  "height": 0.6
})
```
```
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```
```
db.pokemons.insert({
  "name": "Polygon",
  "description": "pato feito em origami",
  "type": "psychic",
  "attack": 90,
  "defense": 60,
  "height": 0.4
})
```
```
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```
```
db.pokemons.insert({
  "name": "Metapod",
  "description": "casulo inquebravel",
  "type": "grama",
  "attack": 32,
  "defense": 60,
  "height": 0.4
})
```
```
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

## 5. Mostrar os pokemons dentro da collection

```
luizcieslak-N150SD-N155SD(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57db1d637933407799dc5d18"),
  "name": "Pikachu",
  "description": "shazam carai",
  "type": "electric",
  "attack": 55,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("57db1d877933407799dc5d19"),
  "name": "Oddish",
  "description": "planta verde mt louca",
  "type": "grama",
  "attack": 60,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("57db1d927933407799dc5d1a"),
  "name": "Starmie",
  "description": "estrela de 8 pontas roxa que solta agua",
  "type": "agua",
  "attack": 80,
  "defense": 50,
  "height": 0.6
}
{
  "_id": ObjectId("57db1df04db19953af64a73d"),
  "name": "Metapod",
  "description": "casulo inquebravel",
  "type": "grama",
  "attack": 32,
  "defense": 60,
  "height": 0.4
}
{
  "_id": ObjectId("57db1e6d4db19953af64a73e"),
  "name": "Polygon",
  "description": "pato feito em origami",
  "type": "psychic",
  "attack": 90,
  "defense": 60,
  "height": 0.4
}
Fetched 5 record(s) in 1ms
```

## 6. Buscar o pokemon
```
var query = {name: 'Pikachu'}
var poke = db.pokemons.findOne(query)
```

## 7. Mudar a description
```
poke.description = "pokemon amarelo que solta raio pela bochecha"
db.pokemons.save(poke)

Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
```
luizcieslak-N150SD-N155SD(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57db1d637933407799dc5d18"),
  "name": "Pikachu",
  "description": "pokemon amarelo que solta raio pela bochecha",
  "type": "electric",
  "attack": 55,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```
