# MongoDB - Aula 03 - Exercício
autor: Leonardo Cassuriaga Lima

## Consultas usando operadores aritméticos

## 1. Liste todos Pokemons com a altura menor que 0.5

var query = { height: { $lt: 0.5}}  
db.pokemons.find(query)  
{  
    "_id": ObjectId("5642766175e5e0f170ca7eda"),  
    "name": "Pikachu",  
    "description": "Rato elétrico bem fofinho",  
    "type": "eletric",  
    "attack": 55,  
    "height": 0.4  
}  
{  
    "_id": ObjectId("5642797375e5e0f170ca7edb"),  
    "name": "Bulbassauro",  
    "description": "Chicote de trepadeira",  
    "type": "grama",  
    "attack": 49,  
    "height": 0.4  
}  
{  
    "_id": ObjectId("56427bcb75e5e0f170ca7ede"),  
    "name": "Caterpie",  
    "description": "Larva lutadora",  
    "type": "inseto",  
    "attack": 30,  
    "height": 0.3,  
    "defense": 35  
}  

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5 

var query = { height: { $gte: 0.5} }  
db.pokemons.find(query)  
{  
    "_id": ObjectId("564279b675e5e0f170ca7edc"),  
    "name": "Charmander",  
    "description": "Esse é o cão chupando manga de fofinho",  
    "type": "fogo",  
    "attack": 52,  
    "height": 0.6  
}  
{  
    "_id": ObjectId("564279e675e5e0f170ca7edd"),  
    "name": "Squirtle",  
    "description": "Ejeta água que passarinho não bebe",  
    "type": "água",  
    "attack": 48,  
    "height": 0.5  
}  
{  
    "_id": ObjectId("564517dc8a8df0148a609971"),  
    "name": "Lickilicky",  
    "description": "Pokemon linguarudo",  
    "type": "normal",  
    "attack": 40,  
    "height": 1.7  
}  
{  
    "_id": ObjectId("564517e28a8df0148a609972"),  
    "name": "Delphox",  
    "description": "Pokemon metido a Xaman",  
    "type": "psychic",  
    "attack": 40,  
    "height": 1.5  
}  
{  
    "_id": ObjectId("564517e78a8df0148a609973"),  
    "name": "Electrike",  
    "description": "Pokemon like a flash(DC)",  
    "type": "eletric",  
    "attack": 20,  
    "height": 0.6  
}  
{  
    "_id": ObjectId("564517ee8a8df0148a609974"),  
    "name": "Scyther",  
    "description": "Cortador de cana eficiente",  
    "type": "bug",  
    "attack": 60,  
    "height": 1.5  
}  


## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

var query = { $and: [{ type: 'grama'}, { height:{ $lte: 0.5} }]}  
db.pokemons.find(query)  
{  
    "_id": ObjectId("5642797375e5e0f170ca7edb"),  
    "name": "Bulbassauro",  
    "description": "Chicote de trepadeira",  
    "type": "grama",  
    "attack": 49,  
    "height": 0.4  
}  

## 4. Liste todos Pokemons com o nome 'Pikachu' OU com attack menor ou igual que 0.5

var query = { $or: [{ name: 'Pikachu'}, { attack: { $lte: 0.5}}]}  
db.pokemons.find(query)  
{  
    "_id": ObjectId("5642766175e5e0f170ca7eda"),  
    "name": "Pikachu",  
    "description": "Rato elétrico bem fofinho",  
    "type": "eletric",  
    "attack": 55,  
    "height": 0.4  
}  

## 5. liste todos Pokemons com attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5

var query = { $and: [{ attack: { $gte: 48}}, { height: { $lte: 0.5}}]}  
db.pokemons.find(query)  
{  
    "_id": ObjectId("5642766175e5e0f170ca7eda"),  
    "name": "Pikachu",  
    "description": "Rato elétrico bem fofinho",  
    "type": "eletric",  
    "attack": 55,  
    "height": 0.4  
}  
{  
    "_id": ObjectId("5642797375e5e0f170ca7edb"),  
    "name": "Bulbassauro",  
    "description": "Chicote de trepadeira",  
    "type": "grama",  
    "attack": 49,  
    "height": 0.4  
}  
{  
    "_id": ObjectId("564279e675e5e0f170ca7edd"),  
    "name": "Squirtle",  
    "description": "Ejeta água que passarinho não bebe",  
    "type": "água",  
    "attack": 48,  
    "height": 0.5  
}  