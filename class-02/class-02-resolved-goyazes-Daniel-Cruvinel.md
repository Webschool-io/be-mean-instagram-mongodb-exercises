# MongoDB - Aula 02 - Exercício
autor: Daniel Cruvinel

## Listagem das databases (passo 2)

    ```
     > use be-mean-pokemons
     switched to db be-mean-pokemons

     > show dbs
    be-mean            0.078GB
    be-mean-instagram  0.078GB
    be-mean-teste      0.078GB
    local              0.078GB

    ```

## Listagem das coleções (passo 3)

    ```
    > show collections
    >

    ```

## Cadastro dos pokemons (passo 4)

    '''
    > var wooper = {'name':'wooper', 'description':'wooper usually lives in water. However, it occasionally comes out  in search of food.', attack:10, defense:9, height:0.4}
    > db.pokemons.insert(wooper)
    WriteResult({ "nInserted" : 1 })

    > var espeon = {'name':'espeon', 'description':'Espeon is extremely loyal to any Trainer it considers to be worthy.', at
    tack: 33, defense: 33, height: 0.9}
    > db.pokemons.insert(espeon)
    WriteResult({ "nInserted" : 1 })

    > var umbreon = {'name':'umbreon', 'description': 'Umbreon evolved as a result of exposure to the moons waves. It hides
    silently in darkness and waits for its foes to make a move.', attack: 33, defense: 55, height: 1}
    > db.pokemons.insert(umbreon)
    WriteResult({ "nInserted" : 1 })

    > var murkrow = {'name':'murkrow','description':'Murkrow was feared and loathed as the alleged bearer of ill fortune. Sh
    ow strong interest in anything that sparkles or glitters.', attack: 40, defense: 20, height: 0.5}
    > db.pokemons.insert(murkrow)
    WriteResult({ "nInserted" : 1 })

    > var unown = {'name':'unown','description':'This pokemon is shaped like ancient writing. It is a mystery as to which ca
    me first, the ancient writings or the various Unown.', attack: 40, defense: 20, height: 0.5}
    > db.pokemons.insert(unown)
    WriteResult({ "nInserted" : 1 })

    > var steelix = {'name':'steelix','description':'Steelix lives even further underground than Onix. Dig toward the earths
    core.', attack: 40, defense: 80, height: 9.2}
    > db.pokemons.insert(steelix)
    WriteResult({ "nInserted" : 1 })

    '''

## Listagem dos pokemons (passo 5)

    '''
    > db.pokemons.find()
    { "_id" : ObjectId("56453e6c9f4571da18d4f325"), 
    "name" : "wooper", 
    "description" : "wooper usually lives in water. However, it occasionally comes out onto land in search of food.", 
    "attack" : 10, 
    "defense" : 9, 
    "height" : 0.4 
    }

    { "_id" : ObjectId("564540129f4571da18d4f326"), 
    "name" : "espeon", 
    "description" : "Espeon is extremely loyal to any Trainer it considers to be worthy.", 
    "attack" : 33, 
    "defense" : 33, 
    "height" : 0.9 
    }

    { "_id" : ObjectId("564540af9f4571da18d4f327"), 
    "name" : "umbreon", 
    "description" : "Umbreon evolved as a result of exposure to the moons waves. It hides silently in darkness and waits for its foes to make a move", 
    "attack" : 33, 
    "defense": 55, 
    "height" : 1 
    }

    { "_id" : ObjectId("564541319f4571da18d4f328"), 
    "name" : "murkrow", 
    "description" : "Murkrow was feared and loathed as the alleged bearer of ill fortune. Show strong interest in anything that sparkles or glitters.", 
    "attack" : 40, 
    "defense": 20, 
    "height" : 0.5 
    }

    { "_id" : ObjectId("564541c59f4571da18d4f329"), 
    "name" : "unown", 
    "description" : "This pokemon is shaped like ancient writing. It is a mystery as to which came first, the ancient writings or the various Unown.", 
    "attack" : 40, 
    "defense" : 20,
    "height" : 0.5 
    }

    { 
        "_id" : ObjectId("564542969f4571da18d4f32a"), 
        "name" : "steelix", 
        "description" : "Steelix lives even further underground than Onix. Dig toward the earths core.", 
        "attack" : 40, 
        "defense" : 80, 
        "height" : 9.2 
    }
    '''

## Pokemon (passo 6)
    '''
    > var query = {'name': 'steelix'}
    > var poke = db.pokemons.findOne(query)
    poke
     { 
        "_id" : ObjectId("564542969f4571da18d4f32a"), 
        "name" : "steelix", 
        "description" : "Steelix lives even further underground than Onix. Dig toward the earths core.", 
        "attack" : 40, 
        "defense" : 80, 
        "height" : 9.2 
    }

    '''

## Pokemon (passo 7)
    '''
    > poke.description
    Steelix lives even further underground than Onix. Dig toward the earths core.

    > poke.description = "Descricao modificada"
    > db.pokemons.save(poke)
    '''