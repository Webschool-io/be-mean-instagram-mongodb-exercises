


# MongoDB - Aula 02 - Exercício
autor: EVELLYN LIMA

## 1. Criar database chamada be-mean-pokemons
```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## 2. Liste quais databases você possui nesse servidor
```
> show dbs
admin              0.000GB
be-mean            0.005GB
be-mean-instagram  0.000GB
be-mean-pokemons   0.000GB
local              0.000GB
teste              0.000GB
```

## 3. Liste quais coleções você possui nessa database
```
> show collections
pokemons
```

## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: nome, description, attack, defense e height
```
var pokemon = {"name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
db.pokemons.insert(pokemon);

var pokemon = { "name" : "Caterpie", "description" : "Larva lindinha", "type" : "inseto", "attack" : 30, "height" : 0.3 }
db.pokemons.insert(pokemon);

var pokemon = { "name" : "Magby", "description" : "Um pato que cospe fogo", "type" : "fogo", "attack" : 35, "height" : 0.7 }
db.pokemons.insert(pokemon);

var pokemon = { "name" : "Treecko", "description" : "Largarto marento estiloso", "type" : "grama", "attack" : 30, "height" : 0.5 }
db.pokemons.insert(pokemon);

var pokemon = { "name" : "Elgyem", "description" : "Largarto marento estiloso", "type" : "psiquica", "attack" : 35, "height" : 0.5 }
db.pokemons.insert(pokemon);
```
## 5. Liste os pokemons existentes na sua coleção
```
> db.pokemons.find()
{ "_id" : ObjectId("584368e4841326e66ea9ebb4"), "name" : "Charizard", "description" : "Dragão muito doido que cospe fogo", "type" : "fogo", "attack" : 223, "height" : 1.7}
{ "_id" : ObjectId("58436949841326e66ea9ebb5"), "name" : "Rattata", "description" : "Rato nervoso e tem em todo lugar", "type" : "normal", "attack" : 103, "height" : 0.3}
{ "_id" : ObjectId("584369a2841326e66ea9ebb6"), "name" : "Meowth", "description" : "Gato doido", "type" : "normal", "attack" : 92, "height" : 0.4}
{ "_id" : ObjectId("584369f0841326e66ea9ebb7"), "name" : "Psyduck", "description" : "Pato fofo doido da porra", "type" : "água", "attack" : 122, "height" : 0.8}
{ "_id" : ObjectId("58436a48841326e66ea9ebb8"), "name" : "Nidorina", "description" : "Muito fofo com cara de bravinho *-*", "type" : "mistico", "attack" : 117, "height" : 0.8}
{ "_id" : ObjectId("584c5db792b43802cf89585a"), "name" : "Pikachu", "description" : "Tato elétrico bem fofinho", "type" : "electic", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("584c5db792b43802cf89585b"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("584c5db792b43802cf89585c"), "name" : "Charmander", "description" : "Esse é o cçao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("584c5db792b43802cf89585e"), "name" : "Caterpie", "description" : "Larva lindinha", "type" : "inseto", "attack" : 30, "height" : 0.3 }
{ "_id" : ObjectId("584c5db792b43802cf89585f"), "name" : "Magby", "description" : "Um pato que cospe fogo", "type" : "fogo", "attack" : 35, "height" : 0.7 }
{ "_id" : ObjectId("584c5db792b43802cf895860"), "name" : "Treecko", "description" : "Largarto marento estiloso", "type" : "grama", "attack" : 30, "height" : 0.5 }
{ "_id" : ObjectId("584c5db792b43802cf895861"), "name" : "Elgyem", "description" : "Largarto marento estiloso", "type" : "psiquica", "attack" : 35, "height" : 0.5 }
```

## 6. Busque um pokemons a sua escolha, pelo nome, e armazene-o em uma variávle chamada `poke`
```
> var updatepoke = {name: "Elgyem"}
> var poke = db.pokemons.findOne(updatepoke)
> poke
{
        "_id" : ObjectId("584c5db792b43802cf895861"),
        "name" : "Elgyem",
        "description" : "Largarto marento estiloso",
        "type" : "psiquica",
        "attack" : 35,
        "height" : 0.5,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
```

## 7. Modifique sua `description` e salvê-o
```
> poke.description = 'Lagarto marrentão'
Lagarto marrentão
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```