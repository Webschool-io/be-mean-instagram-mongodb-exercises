# MongoDB - Aula 03 - Exercício
autor: Laércio Bernardo

## Liste todos Pokemons com a altura menor que 0.5 (passo 1)

```
var query = {height:{$lt:0.5}}
db.pokemons.find(query)
{
        "_id" : ObjectId("56e21ae2d3ec781f3a3b8324"),
        "name" : "Eevee",
        "description" : "Eevee has an unstable genetic makeup that suddenly mutates due to the environment in which it lives. Radiation from various stones causes this Pokémon to evolve.",
        "attack" : 55,
        "defense" : 50,
        "height" : 0.3
}
```

## Liste todos Pokemons com a altura maior ou igual que 0.5 (passo 2)

```
var query = {height:{$gte:0.5}}                        
db.pokemons.find(query)
{                                                        
        "_id" : ObjectId("56e21ae2d3ec781f3a3b8325"),    
        "name" : "Charizard",                            
        "description" : "Charizard flies around the sky i
n search of powerful opponents. It breathes fire of such 
great heat that it melts anything. However, it never turn
s its fiery breath on any opponent weaker than itself.", 
        "attack" : 84,                                   
        "defense" : 78,                                  
        "height" : 1.7                                   
}                                                        
{                                                        
        "_id" : ObjectId("56e21ae2d3ec781f3a3b8326"),    
        "name" : "Blastoise",                            
        "description" : "Blastoise has water spouts that 
protrude from its shell. The water spouts are very accura
te. They can shoot bullets of water with enough accuracy 
to strike empty cans from a distance of over 160 feet.", 
        "attack" : 83,                                   
        "defense" : 100,                                 
        "height" : 1.6                                   
}                                                        
{                                                        
        "_id" : ObjectId("56e21ae2d3ec781f3a3b8327"),    
        "name" : "Venusaur",                             
        "description" : "There is a large flower on Venus
aur's back. The flower is said to take on vivid colors if
 it gets plenty of nutrition and sunlight. The flower's a
roma soothes the emotions of people.",                   
        "attack" : 82,                                   
        "defense" : 83,                                  
        "height" : 6.7                                   
}                                                        
{                                                        
        "_id" : ObjectId("56e21ae2d3ec781f3a3b8328"),    
        "name" : "Mewtwo",                               
        "description" : "Mewtwo is a Pokémon that was cre
ated by genetic manipulation. However, even though the sc
ientific power of humans created this Pokémon's body, the
y failed to endow Mewtwo with a compassionate heart.",   
        "attack" : 110,                                  
        "defense" : 90,                                  
        "height" : 2                                     
}                                                        
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 3)

```
var query = {$and:[{height:{$lte:0.5}},{type:"grama"}]}

db.pokemons.find(query)
```

## Liste todos Pokemons com qualquer nome OU com altura menor ou igual que 0.5 (passo 4)


```
var query = {$or:[{name:"Charizard"},{height:{$lte:0.5}}]}
db.pokemons.find(query)
{
        "_id" : ObjectId("56e21fabd3ec781f3a3b832f"),
        "name" : "Eevee",
        "description" : "Eevee has an unstable genetic makeup that suddenly mutates due to the environment in which it lives. Radiation from various stones causes this Pokémon to evolve.",
        "type" : "Normal",
        "attack" : 55,
        "defense" : 50,
        "height" : 0.3
}
{
        "_id" : ObjectId("56e21fabd3ec781f3a3b8330"),
        "name" : "Charizard",
        "description" : "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
        "type" : "Fogo",
        "attack" : 84,
        "defense" : 78,
        "height" : 1.7
}
> 
```
## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com altura MENOR OU IGUAL QUE 0.5 (passo 5)

```
var query = {$and:[{attack:{$gte:48}},{height:{$lt:0.5}}]}
db.pokemons.find(query)
{
        "_id" : ObjectId("56e21fabd3ec781f3a3b832f"),
        "name" : "Eevee",
        "description" : "Eevee has an unstable genetic makeup that suddenly mutates due to the environment in which it lives. Radiation from various stones causes this Pokémon to evolve.",
        "type" : "Normal",
        "attack" : 55,
        "defense" : 50,
        "height" : 0.3
}
```