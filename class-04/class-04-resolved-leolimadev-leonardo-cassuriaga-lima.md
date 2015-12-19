# MongoDB - Aula 03 - Exercício
autor: Leonardo Cassuriaga Lima

##1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons, Pikachu, Squirtle, Bulbassauro e Charmander.

> var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};  
> var mod = { $pushAll: { moves: ['Dolares no Cunha','Já acabou Jessica?']}};  
> var opts = { multi: true };  
> db.pokemons.update(query, mod, opts);  
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })  

##2. Adicionar 1 movimento em todos os pokemons: 'desvio'.

> var query = {}  
> var mod = { $push: { moves: 'desvio'}};  
> var opts = { multi: true };  
> db.pokemons.update(query, mod, opts);  
WriteResult({ "nMatched" : 11, "nUpserted" : 0, "nModified" : 11 })  

##3. Adicionar o pokemon 'AindaNaoExisteMon' caso ele nao exista com todos os dados com o valor 'null' e a descricao: 'Sem maiores informacoes'.

> var query = { name: /AindaNaoExisteMon/i };  
> var mod = { $setOnInsert: {  
    name: "AindaNaoExisteMon"  
  , attack: null  
  , height: null  
  , defense: null  
  , moves: []  
  , description: "Sem maiores informações"  
}};  
>  
> var query = { name: /AindaNaoExisteMon/i };  
> var mod = { $setOnInsert: {  
    name: "AindaNaoExisteMon"  
  , attack: null  
  , height: null  
  , defense: null  
  , moves: []  
  , description: "Sem maiores informações"  
}};  
> var opts = { upsert: true };  
> db.pokemons.update(query, mod, opts);  
WriteResult({  
    "nMatched" : 0,  
    "nUpserted" : 1,  
    "nModified" : 0,  
    "_id" : ObjectId("564e6e4d960e5f19b9c34285")  
})

##4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que voce adicionou, escolha seu pokemon favorito.

> var query = { moves: { $in: ['investida', /já acabou jessica?/i] }};  
> db.pokemons.find(query);  
{ 
    "_id" : ObjectId("564a739f8fe8159fb9051413"), 
    "name" : "Pikachu", 
    "description" : "Rato elétrico bem fofinho", 
    "type" : "eletric", 
    "attack" : 55, 
    "height" : 0.4, 
    "moves" : 
        [ 
            "Dolares no Cunha", 
            "já acabou Jessica?", 
            "desvio" 
        ] 
}  
{  
     "_id" : ObjectId("564a73b18fe8159fb9051414"), 
     "name" : "Bulbassauro", 
     "description" : "Chicote de trepadeira", 
     "type" : "grama", 
     "attack" : 49, 
     "height" : 0.4, 
     "moves" : 
        [ 
            "Dolares no Cunha", 
            "já acabou Jessica?", 
            "desvio"
        ] 
}
{  
     "_id" : ObjectId("564a73bb8fe8159fb9051415"), 
     "name" : "Charmander", 
     "description" : "Esse é o cão chupando manga de fofinho", 
     "type" : "fogo", 
     "attack" : 52, 
     "height" : 0.6, 
     "moves" : 
        [ 
            "Dolares no Cunha", 
            "já acabou Jessica?", 
            "desvio"
        ] 
}
{  
     "_id" : ObjectId("564a73cb8fe8159fb9051416"), 
     "name" : "Squirtle", 
     "description" : "Ejeta água que passarinho não bebe", 
     "type" : "água", 
     "attack" : 48, 
     "height" : 0.5, 
     "moves" : 
        [ 
            "Dolares no Cunha", 
            "já acabou Jessica?", 
            "desvio"
        ] 
}

##5. Pesquisar todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

> var query = { moves: { $all: [/Dolares no Cunha/i, /Já acabou Jessica?/i, /desvio/i]}}
> db.pokemons.find(query)
{  
    "_id": ObjectId("564a739f8fe8159fb9051413"),  
    "name": "Pikachu",  
    "description": "Rato elétrico bem fofinho",  
    "type": "eletric",  
    "attack": 55,  
    "height": 0.4,  
    "moves": ["Dolares no Cunha", "já acabou Jessica?", "desvio"]  
}  
{  
    "_id": ObjectId("564a73b18fe8159fb9051414"),  
    "name": "Bulbassauro",  
    "description": "Chicote de trepadeira",  
    "type": "grama",  
    "attack": 49,  
    "height": 0.4,  
    "moves": ["Dolares no Cunha", "já acabou Jessica?", "desvio"]  
}
{  
    "_id": ObjectId("564a73bb8fe8159fb9051415"),  
    "name": "Charmander",  
    "description": "Esse é o cão chupando manga de fofinho",  
    "type": "fogo",  
    "attack": 52,  
    "height": 0.6,  
    "moves": ["Dolares no Cunha", "já acabou Jessica?", "desvio"]  
}  
{  
    "_id": ObjectId("564a73cb8fe8159fb9051416"),  
    "name": "Squirtle",  
    "description": "Ejeta água que passarinho não bebe",   
    "type": "água",  
    "attack": 48,  
    "height": 0.5,  
    "moves": ["Dolares no Cunha", "já acabou Jessica?", "desvio"]  
}  



##6. Pesquisar todos os pokemons que nao sao do tipo 'eletrico'.

> var query = { type: {$ne: "eletric"}}  
> db.pokemons.find(query)  
{  
    "_id": ObjectId("56428fe475e5e0f170ca7ee1"),  
    "name": "Delphox",  
    "description": "Pokemon metido a Xaman",  
    "type": "psychic",  
    "attack": 40,  
    "height": 1.5,  
    "moves": ["desvio"]  
}  
{  
    "_id": ObjectId("56428ffb75e5e0f170ca7ee3"),  
    "name": "Scyther",  
    "description": "Praticamente um ceifeiro",  
    "type": "bug",  
    "attack": 60,  
    "height": 1.5,  
    "moves": ["desvio"]  
}  
{  
    "_id": ObjectId("564a73b18fe8159fb9051414"),  
    "name": "Bulbassauro",  
    "description": "Chicote de trepadeira",  
    "type": "grama",  
    "attack": 49,  
    "height": 0.4,  
    "moves": ["Dolares no Cunha", "já acabou Jessica?", "desvio"]  
}  
{   
    "_id": ObjectId("564a73bb8fe8159fb9051415"),  
    "name": "Charmander",  
    "description": "Esse é o cão chupando manga de fofinho",  
    "type": "fogo",  
    "attack": 52,  
    "height": 0.6,  
    "moves": ["Dolares no Cunha", "já acabou Jessica?", "desvio"]  
}  
{  
    "_id": ObjectId("564a73cb8fe8159fb9051416"),  
    "name": "Squirtle",  
    "description": "Ejeta água que passarinho não bebe",  
    "type": "água",  
    "attack": 48,  
    "height": 0.5,  
    "moves": ["Dolares no Cunha", "já acabou Jessica?", "desvio"]  
}  
{  
    "_id": ObjectId("564a73d68fe8159fb9051417"),  
    "name": "Caterpie",  
    "description": "Larva lutadora",  
    "type": "inseto",  
    "attack": 30,  
    "height": 0.3,  
    "defense": 35,  
    "moves": ["desvio"]  
}  
{  
    "_id": ObjectId("564a73e58fe8159fb9051418"),  
    "name": "Haunter",  
    "description": "Pokemon perigoso",  
    "type": "ghost",  
    "attack": 30,  
    "height": 0.16,  
    "moves": ["desvio"]  
}  
{  
    "_id": ObjectId("564a73ef8fe8159fb9051419"),  
    "name": "Lickilicky",  
    "description": "Pokemon linguarudo",  
    "type": "normal",  
    "attack": 40,  
    "height": 1.7,  
    "moves": ["desvio"]  
}  
{  
    "_id": ObjectId("564a76368fe8159fb905141a"),  
    "description": "Pokemon de teste",  
    "name": "Testemon",  
    "attack": 8000,  
    "defense": 800,  
    "moves": ["choque do trovão", ["desvio"]]  
}  
{  
    "_id": ObjectId("564e6e4d960e5f19b9c34285"),  
    "name": "AindaNaoExisteMon",  
    "attack": null,  
    "height": null,  
    "defense": null,  
    "moves": [],  
    "description": "Sem maiores informações"  
}


##7. Pesquisar todos os pokemons que tenha o ataque 'investida' E tenham a defesa nao menor ou igual a  49.

> var queryMoves = { $all: ["investida"]}  
> var queryDef = { $not: { $gte: 49}}  
> var query = { moves: queryMoves, attack: queryDef }  
> db.pokemons.find(query)  

##8. Remova todos os pokemons do tipo agua e com attack menor que 50.

> var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]};  
> db.pokemons.remove(query);  
WriteResult({ "nRemoved" : 1 })  