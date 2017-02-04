# MongoDB - Aula 02 - Exercício
autor: Everton Ferreira Dos Santos 

## Criar database chamada be-mean-pokemons (1)

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases existentes no servidor (2)

```
show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
dbCursoMongoDb    → 0.000GB
local             → 0.000GB
```
## Listagem das collections existentes na database (3)

```
show collections
pokemons → 0.000MB / 0.004MB
```

## Inserção de pokemons (4)

```
var pokemon = {'name':'Pidgey', 'description':'Pidgey tem um sentido de direção extremamente potente. Ele é capaz de voltar para o seu ninho indepndente da distância que esteja', 'type':'vôo', attack: 45, height: 0.3}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 350ms
WriteResult({"nInserted": 1})

var pokemon = {'name':'Wartortle', 'description':'Sua calda é coberta com uma pele bem espessa. É um Pokemon combatente', 'type':'água', attack: 63, height: 1}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({"nInserted": 1})

var pokemon = {'name':'Charmeleon', 'description':'Destroi seus inimigos usando suas garras afiadas', 'type':'fogo', attack: 64, height: 1.1}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({"nInserted": 1})

var pokemon = {'name':'Raticate', 'description':'Presas crescem de forma constante. Pode mastigar paredes de casas', 'type':'normal', attack: 81, height: 0.7}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({"nInserted": 1})

var pokemon = {'name':'Arcanine', 'description':'Possue alta velocidade. Pode ser capaz de percorrer 6200 milhas em um único dia', 'type':'fogo', attack: 110, height: 1.9}
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({"nInserted": 1})
```

## Listando pokemons existentes na coleção (5)

```
db.pokemons.find()
{                                                                                                   
  "_id": ObjectId("586c5c35dea52c3bfa912150"),                                                      
  "name": "Pidgey",                                                                                 
  "description": "Pidgey tem um sentido de direção extremamente potente. Ele é capaz de voltar para 
  "type": "vôo",                                                                                    
  "attack": 45,                                                                                     
  "height": 0.3                                                                                     
}                                                                                                   
{                                                                                                   
  "_id": ObjectId("586c5ff2dea52c3bfa912151"),                                                      
  "name": "Wartortle",                                                                              
  "description": "Sua calda é coberta com uma pele bem espessa. É um Pokemon combatente",           
  "type": "água",                                                                                   
  "attack": 63,                                                                                     
  "height": 1                                                                                       
}                                                                                                   
{                                                                                                   
  "_id": ObjectId("586c614cdea52c3bfa912152"),                                                      
  "name": "Charmeleon",                                                                             
  "description": "Destroi seus inimigos usando suas garras afiadas",                                
  "type": "fogo",                                                                                   
  "attack": 64,                                                                                     
  "height": 1.1                                                                                     
}                                                                                                   
{                                                                                                   
  "_id": ObjectId("586c62c5dea52c3bfa912153"),                                                      
  "name": "Raticate",                                                                               
  "description": "Presas crescem de forma constante. Pode mastigar paredes de casas",               
  "type": "normal",                                                                                 
  "attack": 81,                                                                                     
  "height": 0.7                                                                                     
}                                                                                                   
{                                                                                                   
  "_id": ObjectId("586c641ddea52c3bfa912154"),                                                      
  "name": "Arcanine",                                                                               
  "description": "Possue alta velocidade. Pode ser capaz de percorrer 6200 milhas em um único dia", 
  "type": "fogo",                                                                                   
  "attack": 110,                                                                                    
  "height": 1.9                                                                                     
}                                                                                                   
Fetched 5 record(s) in 195ms 
```          

## Query de busca pokemon (6)

```
var query = {name:'Pidgey'}
var poke = db.pokemons.findOne(query)
poke

{                                                                                                                                                    
  "_id": ObjectId("586c5c35dea52c3bfa912150"),                                                                                                       
  "name": "Pidgey",                                                                                                                                  
  "description": "Pidgey tem um sentido de direção extremamente potente. Ele é capaz de voltar para o seu ninho indepndente da distância que esteja",
  "type": "vôo",                                                                                                                                     
  "attack": 45,                                                                                                                                      
  "height": 0.3                                                                                                                                      
}                                                                                                                         
Fetched 1 record(s) in 5ms
```

## Modificação da descrição e salvando pokemon (7)

``` 
poke.description = 'Alterada description pokemon Pidgey'
db.pokemons.save(poke)
Updated 1 existing record(s) in 146ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

