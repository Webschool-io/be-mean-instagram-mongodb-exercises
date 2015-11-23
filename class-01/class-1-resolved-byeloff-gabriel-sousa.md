
## Importando os restaurantes

    MacBook-Pro-de-user:mongodb Byel$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-22T21:12:17.041-0200    connected to: localhost
    2015-11-22T21:12:17.072-0200    dropping: be-mean.restaurantes
    2015-11-22T21:12:19.910-0200    [##########..............] be-mean.restaurantes5.2 MB/11.4 MB (45.5%)
    2015-11-22T21:12:22.498-0200    imported 25359 documents

## Contando os restaurantes

    MacBook-Pro-de-user(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
    25359