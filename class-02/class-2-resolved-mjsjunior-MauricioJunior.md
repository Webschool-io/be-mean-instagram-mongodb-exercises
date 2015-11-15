# MongoDB - Aula 02 - Exercício
autor: Maurício José da Silva Júnior

## Criando database pokemons
```
mjunior(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons
mjunior(mongod-3.0.7) be-mean-pokemons> 
```

## Listagem das databases (passo 2)
```
mjunior(mongod-3.0.7) be-mean-pokemons> show databases
    contactlist       → 0.203GB
    be-mean-instagram → 0.078GB
    local             → 0.078GB
    admin             → 0.078GB
    todos             → 0.078GB
mjunior(mongod-3.0.7) be-mean-pokemons> 
```

## Listagem das coleções (passo 3)
```
mjunior(mongod-3.0.7) be-mean-pokemons> show collections
mjunior(mongod-3.0.7) be-mean-pokemons> 
```
## Cadastro dos pokemons (passo 4)
```
mjunior(mongod-3.0.7) be-mean-pokemons> poke1 = {
... name:'1 - Bulbasaur',
... description: 'Coloquei o numero na frente do nome pra na hora da listagem ser mais facil de encontrar esse bicho de nome dificil rs', 
... attack: 49, 
... defense: 49,
... height: 7
... }
{
  "name": "1 - Bulbasaur",
  "description": "Coloquei o numero na frente do nome pra na hora da listagem ser mais facil de encontrar esse bicho de nome dificil rs",
  "attack": 49,
  "defense": 49,
  "height": 7
}
mjunior(mongod-3.0.7) be-mean-pokemons> 
mjunior(mongod-3.0.7) be-mean-pokemons> poke2 = {
... name:'2 - Ivysaur',
... description: 'Também nem conheço esse bicho.', 
... attack: 62, 
... defense: 63,
... height: 10
... }
{
  "name": "2 - Ivysaur",
  "description": "Também nem conheço esse bicho.",
  "attack": 62,
  "defense": 63,
  "height": 10
}
mjunior(mongod-3.0.7) be-mean-pokemons> poke3 = {
... name:'3 - Venusaur',
... description: 'Esse aqui é doido, mais forte ate agora, tem dobro do tamanho do anterior.. IRRAH!', 
... attack: 82, 
... defense: 83,
... height: 20
... }
{
  "name": "3 - Venusaur",
  "description": "Esse aqui é doido, mais forte ate agora, tem dobro do tamanho do anterior.. IRRAH!",
  "attack": 82,
  "defense": 83,
  "height": 20
}
mjunior(mongod-3.0.7) be-mean-pokemons> poke4 = {
... name:'4 - Charmander',
... description: 'Charmander chaaaaaa!', 
... attack: 52, 
... defense: 43,
... height: 6
... }
{
  "name": "4 - Charmander",
  "description": "Charmander chaaaaaa!",
  "attack": 52,
  "defense": 43,
  "height": 6
}
mjunior(mongod-3.0.7) be-mean-pokemons> poke5 = {
... name:'5 - Charmeleon',
... description: 'Charmander cameleao aiuewh!', 
... attack: 64, 
... defense: 58,
... height: 11
... }
{
  "name": "5 - Charmeleon",
  "description": "Charmander cameleao aiuewh!",
  "attack": 64,
  "defense": 58,
  "height": 11
}


mjunior(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert([poke1,poke2,poke3,poke4,poke5])
Inserted 1 record(s) in 38ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
mjunior(mongod-3.0.7) be-mean-pokemons> 


```
## Lista dos pokemons (passo 5)
```
mjunior(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({})
{
  "_id": ObjectId("56464c17ebe04ad0709ab21c"),
  "name": "1 - Bulbasaur",
  "description": "Coloquei o numero na frente do nome pra na hora da listagem ser mais facil de encontrar esse bicho de nome dificil rs",
  "attack": 49,
  "defense": 49,
  "height": 7
}
{
  "_id": ObjectId("56464c17ebe04ad0709ab21d"),
  "name": "2 - Ivysaur",
  "description": "Também nem conheço esse bicho.",
  "attack": 62,
  "defense": 63,
  "height": 10
}
{
  "_id": ObjectId("56464c17ebe04ad0709ab21e"),
  "name": "3 - Venusaur",
  "description": "Esse aqui é doido, mais forte ate agora, tem dobro do tamanho do anterior.. IRRAH!",
  "attack": 82,
  "defense": 83,
  "height": 20
}
{
  "_id": ObjectId("56464c17ebe04ad0709ab21f"),
  "name": "4 - Charmander",
  "description": "Charmander chaaaaaa!",
  "attack": 52,
  "defense": 43,
  "height": 6
}
{
  "_id": ObjectId("56464c17ebe04ad0709ab220"),
  "name": "5 - Charmeleon",
  "description": "Charmander cameleao aiuewh!",
  "attack": 64,
  "defense": 58,
  "height": 11
}
Fetched 5 record(s) in 4ms
mjunior(mongod-3.0.7) be-mean-pokemons> 



```

## Busca de pokemon por nome (passo 6)
```
mjunior(mongod-3.0.7) be-mean-pokemons> poke = db.pokemons.findOne({name: '5 - Charmeleon'})
{
  "_id": ObjectId("56464c17ebe04ad0709ab220"),
  "name": "5 - Charmeleon",
  "description": "Charmander cameleao aiuewh!",
  "attack": 64,
  "defense": 58,
  "height": 11
}
mjunior(mongod-3.0.7) be-mean-pokemons> 
mjunior(mongod-3.0.7) be-mean-pokemons> poke = db.pokemons.findOne({name: '5 - Charmeleon'})
{
  "_id": ObjectId("56464c17ebe04ad0709ab220"),
  "name": "5 - Charmeleon",
  "description": "Charmander cameleao aiuewh!",
  "attack": 64,
  "defense": 58,
  "height": 11
}
mjunior(mongod-3.0.7) be-mean-pokemons> poke.description = 'Editando o pokemon numero CINCOOOOH :DD'
Editando o pokemon numero CINCOOOOH :DD
mjunior(mongod-3.0.7) be-mean-pokemons> 
mjunior(mongod-3.0.7) be-mean-pokemons> 
mjunior(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 97ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
mjunior(mongod-3.0.7) be-mean-pokemons> 
```

## Atualização do Pikachu (passo 6)

```
mjunior(mongod-3.0.7) be-mean-pokemons> poke = db.pokemons.findOne({name: '5 - Charmeleon'})
{
  "_id": ObjectId("56464c17ebe04ad0709ab220"),
  "name": "5 - Charmeleon",
  "description": "Editando o pokemon numero CINCOOOOH :DD",
  "attack": 64,
  "defense": 58,
  "height": 11
}
mjunior(mongod-3.0.7) be-mean-pokemons> 

```