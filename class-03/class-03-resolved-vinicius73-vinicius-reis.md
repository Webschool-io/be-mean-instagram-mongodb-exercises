# MongoDB - Aula 03 - Exercício
Autor: Vinicius Reis

## 1. Liste todos Pokemons com a altura menor que 0.5;

```
zaraki(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt:0.5}}
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fd"),
  "name": "Suissamon",
  "description": "Loko mais legal",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 0.4,
}
Fetched 1 record(s) in 1ms
zaraki(mongod-3.0.7) be-mean-pokemons>

```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
zaraki(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte:0.5}}
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fe"),
  "name": "Dilmamon",
  "description": "Pokemon presidANTA",
  "type": "besta",
  "attack": 1,
  "defense": 1,
  "height": 1.6
}
{
  "_id": ObjectId("56507b416f97e66bd9f5d6ff"),
  "name": "Cunhamon",
  "description": "Filho da rapariga",
  "type": "besta",
  "attack": 9990,
  "defense": 9999,
  "height": 1.8
}
{
  "_id": ObjectId("56507b416f97e66bd9f5d700"),
  "name": "Calheirosmon",
  "description": "Irmão do filho da rapariga",
  "type": "besta",
  "attack": 8500,
  "defense": 9999,
  "height": 1.79
}
{
  "_id": ObjectId("56507b416f97e66bd9f5d701"),
  "name": "FeliciANUS",
  "description": "Pastor...",
  "type": "besta",
  "attack": 666,
  "defense": 666,
  "height": 1.7
}
Fetched 4 record(s) in 4ms
```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
zaraki(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{height: {$lte:0.5}}, {type:'grama'}]}
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fe"),
  "name": "Dilmamon",
  "description": "Pokemon presidANTA",
  "type": "grama",
  "attack": 1,
  "defense": 1,
  "height": 0.5
}
Fetched 1 record(s) in 2ms
zaraki(mongod-3.0.7) be-mean-pokemons>
```

## 4. Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5;

```
zaraki(mongod-3.0.7) be-mean-pokemons> var query = {$or:[{attack: {$lte:0.5}}, {name:'Pikachu'}]}
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fe"),
  "name": "Dilmamon",
  "description": "Pokemon presidANTA",
  "type": "grama",
  "attack": 0.5,
  "defense": 1,
  "height": 0.5
}
Fetched 1 record(s) in 1ms
zaraki(mongod-3.0.7) be-mean-pokemons>

```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
zaraki(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{attack: {$gte:48}}, {height:{$lte:0.5}}]}
zaraki(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56507b416f97e66bd9f5d6fd"),
  "name": "Suissamon",
  "description": "Loko mais legal",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 0.4,
  "heigth": 0.4
}
Fetched 1 record(s) in 1ms
zaraki(mongod-3.0.7) be-mean-pokemons>
```
