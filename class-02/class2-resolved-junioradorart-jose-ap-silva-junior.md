# MongoDB - Aula 02 - Exercício
autor: José Aparecido da Silva Junior

## Listagem das databases (passo 2)

```
> show dbs
admin              (empty)
be-mean            0.078GB
be-mean-instagram  0.078GB
bemean             0.078GB
local              0.078GB

```


## Listagem das coleções (passo 3)

```
> show collections
> 

```

## Cadastro dos pokemons (passo 4)

```
var pokemon = {'name':'Arbok','description':'Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo','type':'Poison', attack: 65 , height: 3.5 }
db.pokemons.insert(pokemon)

var pokemon = {'name':'Wurmple','description': 'Descasca a casca das árvores e se alimenta de seiva que escorre para fora','type':'Bug', attack: 35 , height: 0.3 }
db.pokemons.insert(pokemon)

var pokemon = {'name':'Zigzagoon','description': 'Inquieto vagueia em todos os lugares em todos os momentos','type':'Normal', attack: 45 , height: 0.4 }
db.pokemons.insert(pokemon)

var pokemon = {'name':'Blastoise','description': 'Tem bicas de água que se projetam de sua concha','type':'Water', attack: 75 , height: 1.6 }
db.pokemons.insert(pokemon)

var pokemon = {'name':'Raichu','description':'Raichu plantas a cauda no chão e descargas','type':'Electric', attack: 55 , height: 0.8 }
db.pokemons.insert(pokemon)


```

## Lista dos pokemons (passo 5)

```
> db.pokemons.find()
{
  "_id": ObjectId("5643fbcdcba869323ecad2a4"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
{
  "_id": ObjectId("5643fd57cba869323ecad2a7"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("5643fd05cba869323ecad2a6"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("5643fdaccba869323ecad2a8"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("5643fc5bcba869323ecad2a5"),
  "name": "Raichu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
Fetched 5 record(s) in 8ms

```

## Blastoise (passo 6)

```
> var query = {'name': 'Raichu'}
> var poke = db.pokemons.findOne(query)
> poke
{
  "_id": ObjectId("5643fc5bcba869323ecad2a5"),
  "name": "Raichu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}


```

## Atualização do Raichu (passo 6)

```
> poke.description = 'Raichu é a evolução do pikachu.'
Raichu é a evolução do pikachu.
> poke
{
  "_id": ObjectId("5643fc5bcba869323ecad2a5"),
  "name": "Raichu",
  "description": "Raichu é a evolução do pikachu",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
> db.pokemons.save(poke)
Updated 1 existing record(s) in 23ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```