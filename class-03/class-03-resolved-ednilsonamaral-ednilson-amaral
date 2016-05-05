# MongoDB - Aula 03 - Exercício


1. Pokemons com height $lt 5
-----------------------------

```  
be-mean-pokemons> var query = {height: {$lt: 0.5}}  
EDNILSON-NB(mongod-3.2.0-rc2-143-gdeaf4af) be-mean-pokemons> db.pokemons.find(query)  
Fetched 0 record(s) in 1ms  
```


2. Pokemons com height $gte 5
------------------------------

```  
be-mean-pokemons> var query = {height: {$gte: 0.5}}  
EDNILSON-NB(mongod-3.2.0-rc2-143-gdeaf4af) be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("5644da2d329b6e6a8376bd42"),  
  "name": "Rampardos",  
  "description": "Pode levar qualquer cascudo na cabeça que não vai sentir porra nenhuma",  
  "type": "rocha",  
  "attack": 165,  
  "defense": 60,  
  "height": 1.6  
}  
{  
  "_id": ObjectId("5644da44329b6e6a8376bd43"),  
  "name": "Slaking",  
  "description": "Pense em um cara preguiçoso, é esse pokebola aí",  
  "type": "normal",  
  "attack": 160,  
  "defense": 100,  
  "height": 2  
}  
{  
  "_id": ObjectId("5644da4e329b6e6a8376bd44"),  
  "name": "Haxorus",  
  "description": "Esse é dócil viu, mas se baixar a pomba gira nele, fica muito agressivo",  
  "type": "dragão",  
  "attack": 147,  
  "defense": 90,  
  "height": 1.8  
}  
{  
  "_id": ObjectId("5644da5a329b6e6a8376bd45"),  
  "name": "Rhyperior",  
  "description": "Esse resiste até a erupções",  
  "type": "rocha",  
  "attack": 140,  
  "defense": 130,  
  "height": 2.4  
}  
{  
  "_id": ObjectId("5644da63329b6e6a8376bd46"),  
  "name": "Metagross",  
  "description": "Esse não tem Windows como SO",  
  "type": "psíquico",  
  "attack": 135,  
  "defense": 130,  
  "height": 1.6  
}  
Fetched 5 record(s) in 6ms  
```


3. Pokemons com height $lte 0.5 $and tipo grama
------------------------------------------------

```  
be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: 'rocha'}]}  
EDNILSON-NB(mongod-3.2.0-rc2-143-gdeaf4af) be-mean-pokemons> db.pokemons.find(query)  
Fetched 0 record(s) in 1ms  
```


4. Pokemons com name 'Pikachu' $or attack $lte 0.5
---------------------------------------------------

```
be-mean-pokemons> var query = {$or: [{name:'Pikachu'}, {height: {$lte: 0.5}}]}  
EDNILSON-NB(mongod-3.2.0-rc2-143-gdeaf4af) be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("56450d4ceecf225922d9bed0"),  
  "name": "Pikachu",  
  "description": "Rato elétrico bem fofinho!"  
}  
Fetched 1 record(s) in 2ms    
```


5. Pokemons com attack $gte 48 $and height $lte 0.5
----------------------------------------------------

```  
be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}  
EDNILSON-NB(mongod-3.2.0-rc2-143-gdeaf4af) be-mean-pokemons> db.pokemons.find(query)  
Fetched 0 record(s) in 1ms  
```