# MongoDB - Aula 01 - Exercício
autor: Henrique Nascimento

## Importando os restaurantes

    mongo --db be-mean --collection restaurantes --host localhost:27017 --drop --file restaurantes.json
    connected to: 127.0.0.1
    2016-12-26T21:18:04.115-0300   connected to: 127.0.0.1
    2016-12-26T21:18:04.119-0300    dropping: be-mean.restaurantes
    2016-12-26T21:18:05.160-0300    imported 25359 documents

## Contando os restaurantes

    use be-mean man
    db.restaurantes.find({}).count()
    25359
