# MongoDB - Aula 02 - Exercício
autor: Namor Alves

## Crie uma database chamada be-mean-pokemons

    ```
Namor-PC(mongod-3.2.1) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
    ```

## Liste quais databases você possui nesse servidor

    ```
Namor-PC(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean            0.004GB
be-mean-instagram  0.000GB
local              0.000GB
    ```
## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

    ```
Namor-PC(mongod-3.2.1) be-mean-pokemons> var listaPokemons = [{'name':'Charizard
','description': 'Charizard flies around the sky in search of powerful opponents
','type': 'fire', 'attack': 109, height: 17 }, {name: "Butterfree", description:
 "Flying", attack: 45, defense: 50, heigth: 1.09}, {name: "Rattatá", description
: "Normal", attack: 56, defense: 35, heigth: 0.30}, {'name':'Blastoise','descrip
tion': 'Blastoise has water spouts that protrude from its shell','type': 'water'
, 'attack': 85, height: 16 }, {'name':'Zubat','description':'Morcego troll','typ
e': 'flying', 'attack': 45, height: 8, 'defense': 35}]                          
Namor-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(listaPokemons)      
Inserted 1 record(s) in 141ms                                                   
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
    ```    
## Liste os pokemons existentes na sua coleção

    ```
Namor-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
{
    "_id": ObjectId("56ba3c25ff3683370d6b971e"),
    "name": "Charizard",
    "description": "Charizard flies around the sky in search of powerful opponents",
    "type": "fire",
    "attack": 109,
    "height": 17
}
{
    "_id": ObjectId("56ba3c25ff3683370d6b971f"),
    "name": "Butterfree",
    "description": "Flying",
    "attack": 45,
    "defense": 50,
    "heigth": 1.09
}
{
    "_id": ObjectId("56ba3c25ff3683370d6b9720"),
    "name": "Rattatá",
    "description": "Normal",
    "attack": 56,
    "defense": 35,
    "heigth": 0.3
}
{
    "_id": ObjectId("56ba3c25ff3683370d6b9721"),
    "name": "Blastoise",
    "description": "Blastoise has water spouts that protrude from its shell",
    "type": "water",
    "attack": 85,
    "height": 16
}
{
    "_id": ObjectId("56ba3c25ff3683370d6b9722"),
    "name": "Zubat",
    "description": "Morcego troll",
    "type": "flying",
    "attack": 45,
    "height": 8,
    "defense": 35
}
Fetched 5 record(s) in 25ms
    ```   
## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`

    ```
Namor-PC(mongod-3.2.1) be-mean-pokemons> var query = {name: 'Zubat'}
Namor-PC(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Namor-PC(mongod-3.2.1) be-mean-pokemons> poke
{
    "_id": ObjectId("56ba3c25ff3683370d6b9722"),
    "name": "Zubat",
    "description": "Morcego troll",
    "type": "flying",
    "attack": 45,
    "height": 8,
    "defense": 35
}
    ```    
## Modifique sua `description` e salvê-o

    ```
Namor-PC(mongod-3.2.1) be-mean-pokemons> poke.description = 'Nova descrição para esse pokemon Batman!'
Nova descrição para esse pokemon Batman!
Namor-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})
Namor-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.findOne(query)
{
    "_id": ObjectId("56ba3c25ff3683370d6b9722"),
    "name": "Zubat",
    "description": "Nova descrição para esse pokemon Batman!",
    "type": "flying",
    "attack": 45,
    "height": 8,
    "defense": 35
}
    ```   
