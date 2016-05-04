# MongoDB - Aula 03 - Exercício
    autor: Thiago Santos de Amorim

## Selecionando o banco be-mean-pokemons criado na aula 02 (passo 1)

```
use be-mean-instagram
switched to db be-mean-instagram
```

## Listagem de todos os Pokemons com a altura menor que 0.5 (passo 2)

```
db.pokemons.find({height:{$lt:0.5}})
{
  "_id": ObjectId("56c8511666474f6c67d13845"),
  "nome": "Pikachu",
  "description": "Rato Elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56c8517666474f6c67d13846"),
  "nome": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
```

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5 (passo 3)

```
db.pokemons.find({$and:[{height:{$lte:0.5}},{type:'grama'}]})
{
  "_id": ObjectId("56c8517666474f6c67d13846"),
  "nome": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 3ms
```

## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 4)

```
db.pokemons.find({$and:[{height:{$lte:0.5}},{type:'grama'}]})
{
  "_id": ObjectId("56c8517666474f6c67d13846"),
  "nome": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 3ms
```

## Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5 (passo 5)

```
var query = {$or:[{nome:'Pikachu'},{attack:{$lte:0.5}}]}
linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c8511666474f6c67d13845"),
  "nome": "Pikachu",
  "description": "Rato Elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 2ms

```
## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 6)

```
linux-atsn(mongod-3.2.1) be-mean-instagram> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c8511666474f6c67d13845"),
  "nome": "Pikachu",
  "description": "Rato Elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56c8517666474f6c67d13846"),
  "nome": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56c851e766474f6c67d13848"),
  "nome": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 5ms
```
