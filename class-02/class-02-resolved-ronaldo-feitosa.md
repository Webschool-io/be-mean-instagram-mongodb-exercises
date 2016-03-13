# MongoDB - Aula 02 - Exercício
autor: Ronaldo Feitosa

## 1 - Crie uma database chamada be-mean-pokemons

	```
> use be-mean-pokemons
switched to db be-mean-pokemons

    ```

## 2 - Liste quais databases possui no servidor

    ```
> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
be-mean-pokemons   0.078GB
local              0.078GB

    
    ```

## 3 - Liste quais coleções possui nesta database

	
    ```
> show collections 
system.indexes
teste

    ```

 ## 4 - Insira pelo menos 5 pokemons utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height


    ```
> var pokemon = {'name':'Kadabra', 'description':'Pokemon Psíquico', 'type':'psíquico', 'height':4.3,'attack':35, 'defense':30}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 
> var pokemon = {'name':'Cubone', 'description':'Pokemon cabeça de Osso', 'type':'terra', 'height':1.4,'attack':50, 'defense':95}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 
> var pokemon = {'name':'Vaporeon', 'description':'Pokemon aquático evoluído do Eevee', 'type':'água', 'height':3.3,'attack':65, 'defense':60}
> 
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 
> var pokemon = {'name':'Butterfree', 'description':'Pokemon voador', 'type':'vento', 'height':3.7,'attack':45, 'defense':50}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 
> var pokemon = {'name':'Golbat', 'description':'Morcego sanguinário', 'type':'vento e veneno', 'height':5.3,'attack':80, 'defense':70}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

    ```

## 5 - Liste os pokemons existentes na sua coleção


    ```
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56e5be841ed08ada9f1ebe73"),
  "name": "Mewtwo",
  "description": "Pokemon super poderoso",
  "type": "psíquico",
  "height": "6.7",
  "attack": 110,
  "defense": 90
}
{
  "_id": ObjectId("56e5bef71ed08ada9f1ebe74"),
  "name": "Kadabra",
  "description": "Pokemon Psíquico",
  "type": "psíquico",
  "height": 4.3,
  "attack": 35,
  "defense": 30
}
{
  "_id": ObjectId("56e5bfe41ed08ada9f1ebe75"),
  "name": "Cubone",
  "description": "Pokemon cabeça de Osso",
  "type": "terra",
  "height": 1.4,
  "attack": 50,
  "defense": 95
}
{
  "_id": ObjectId("56e5c0c61ed08ada9f1ebe76"),
  "name": "Vaporeon",
  "description": "Pokemon aquático evoluído do Eevee",
  "type": "água",
  "height": 3.3,
  "attack": 65,
  "defense": 60
}
{
  "_id": ObjectId("56e5c0ff1ed08ada9f1ebe77"),
  "name": "Butterfree",
  "description": "Pokemon voador",
  "type": "vento",
  "height": 3.7,
  "attack": 45,
  "defense": 50
}
{
  "_id": ObjectId("56e5c1931ed08ada9f1ebe78"),
  "name": "Golbat",
  "description": "Morcego sanguinário",
  "type": "vento e veneno",
  "height": 5.3,
  "attack": 80,
  "defense": 70
}

    ```

6 - Busque os pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada poke


    ```
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> var query = {name : 'Kadabra'}

ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> var poke = db.pokemons.findOne(query)
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> poke
{
  "_id": ObjectId("56e5bef71ed08ada9f1ebe74"),
  "name": "Kadabra",
  "description": "Pokemon Psíquico",
  "type": "psíquico",
  "height": 4.3,
  "attack": 35,
  "defense": 30
}

    ```

7 - Modifique a sua description e salve-o


    ```
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> poke.description = 'Mestre das colheres tortas'
Mestre das colheres tortas
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> 
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> poke
{
  "_id": ObjectId("56e5bef71ed08ada9f1ebe74"),
  "name": "Kadabra",
  "description": "Mestre das colheres tortas",
  "type": "psíquico",
  "height": 4.3,
  "attack": 35,
  "defense": 30
}
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 94ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

    ```

