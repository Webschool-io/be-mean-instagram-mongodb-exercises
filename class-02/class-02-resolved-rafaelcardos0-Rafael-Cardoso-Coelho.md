# MongoDB - Aula 02 - Exercício
autor: RAFAEL CARDOSO COELHO

## 1. Criando uma tabela chamada be-mean-pokemons
```
use be-mean-pokemons

switched to db be-mean-pokemons
```

## 2. Listando as databases existentes no servidor
```
show dbs

be-mean-instagram  0.078GB
be-mean            0.078GB
local              0.078GB
```

## 3. Listando as coleções existentes na database
```
show collections

pokemons        0.001MB / 0.008MB
system.indexes  0.000MB / 0.008MB
```

## 4. Inserindo pokemons
```
db.pokemons.insert({"name": "Pikachu", "description": "Ratinho elétrico amarelo", "attack": 55, "defense": 40, "height": 0.41})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

db.pokemons.insert({"name": "Charizard", "description": "Dragão foda cuspidor de fogo", "attack": 84, "defense": 78, "height": 1.7})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

db.pokemons.insert({"name": "Cartepie", "description": "Lagartinha marota", "attack": 30, "defense": 35, "height": 0.3})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

db.pokemons.insert({"name": "Jigglypuff", "description": "Kirby de franja cantor", "attack": 45, "defense": 20, "height": 0.51})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

db.pokemons.insert({"name": "Snorlax", "description": "Pokemon gordo sedentário", "attack": 110, "defense": 65, "height": 2.11})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```

## 5. Listando todos os pokemons existentes na coleção
```
db.pokemons.find()

{
    "_id": ObjectId("567d940bdc3c391d5ec3769b"),
    "name": "Pikachu",
    "description": "Ratinho elétrico amarelo",
    "attack": 55,
    "defense": 40,
    "height": 0.41
}
{
    "_id": ObjectId("567d9484dc3c391d5ec3769c"),
    "name": "Charizard",
    "description": "Dragão foda cuspidor de fogo",
    "attack": 84,
    "defense": 78,
    "height": 1.7
}
{
    "_id": ObjectId("567d94d1dc3c391d5ec3769d"),
    "name": "Cartepie",
    "description": "Lagartinha marota",
    "attack": 30,
    "defense": 35,
    "height": 0.3
}
{
    "_id": ObjectId("567d952cdc3c391d5ec3769e"),
    "name": "Jigglypuff",
    "description": "Kirby de franja cantor",
    "attack": 45,
    "defense": 20,
    "height": 0.51
}
{
    "_id": ObjectId("567d9581dc3c391d5ec3769f"),
    "name": "Snorlax",
    "description": "Pokemon gordo sedentário",
    "attack": 110,
    "defense": 65,
    "height": 2.11
}
Fetched 5 record(s) in 5ms
```

## 6. Buscando um pokemon e o armazenando em uma variável chamada poke
```
var poke = db.pokemons.findOne({name: "Snorlax"})
```

## 7. Atualizando o atributo *description* do pokemon pesquisado
```
poke.description = "Pokemon gordinho"
db.pokemons.save(poke)

Updated 1 existing record(s) in 3ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})

```