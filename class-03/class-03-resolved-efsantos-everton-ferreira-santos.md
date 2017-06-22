# MongoDB - Aula 03 - Exercício
autor: Everton Ferreira Dos Santos 

## (1) Listagem de pokemons com altura menor que 0.5 

```
var query = {height:{$lt:0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("586b04441ea9448f2ec30694"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("586b05c71ea9448f2ec30695"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("586b09191ea9448f2ec30698"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 20ms                         
```

## (2) Listagem de pokemons com altura maior ou igual que 0.5 

```
var query = {height:{$gte:0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("586b064c1ea9448f2ec30696"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("586b07211ea9448f2ec30697"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 16ms
```
## (3) Listagem de pokemons com altura menor ou igual 0.5 e do tipo grama

```
var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
db.pokemons.find(query)
{
  "_id": ObjectId("586b05c71ea9448f2ec30695"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 6ms
```

## (4) Listagem de pokemons com o name 'Pikachu' ou com attack menor ou igual a 0.5

```
var query = {$or:[{name:'Pikachu'},{attack:{$lte:0.5}}]}
db.pokemons.find(query)
{                                               
  "_id": ObjectId("586b04441ea9448f2ec30694"),  
  "name": "Pikachu",                            
  "description": "Rato elétrico bem fofinho",   
  "type": "electric",                           
  "attack": 55,                                 
  "height": 0.4                                 
}                                               
Fetched 1 record(s) in 7ms                      
```
## (5) Listagem de pokemons com attack maior ou igual a 48 e com height menor ou igual que 0.5

```

var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
db.pokemons.find(query)
{                                                        
  "_id": ObjectId("586b04441ea9448f2ec30694"),           
  "name": "Pikachu",                                     
  "description": "Rato elétrico bem fofinho",            
  "type": "electric",                                    
  "attack": 55,                                          
  "height": 0.4                                          
}                                                        
{                                                        
  "_id": ObjectId("586b05c71ea9448f2ec30695"),           
  "name": "Bulbassauro",                                 
  "description": "Chicote de trepadeira",                
  "type": "grama",                                       
  "attack": 49,                                          
  "height": 0.4                                          
}                                                        
{                                                        
  "_id": ObjectId("586b07211ea9448f2ec30697"),           
  "name": "Squirtle",                                    
  "description": "Ejeta água que passarinho não bebe",   
  "type": "água",                                        
  "attack": 48,                                          
  "height": 0.5                                          
}                                                        
Fetched 3 record(s) in 27ms
```                              


