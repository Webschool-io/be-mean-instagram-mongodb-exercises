# MongoDB - Aula 01 - Exercício
autor: Victor Pereira

## Importando os restaurantes

    mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-14T05:32:41.299+0000    connected to: localhost
    2015-11-14T05:32:41.313+0000    dropping: be-mean.restaurantes
    2015-11-14T05:32:44.299+0000    [########................] be-mean.restaurantes 4.2 MB/11.3 MB (37.2%)
    2015-11-14T05:32:47.297+0000    [#############...........] be-mean.restaurantes 6.6 MB/11.3 MB (58.0%)
    2015-11-14T05:32:50.293+0000    [####################....] be-mean.restaurantes 9.8 MB/11.3 MB (86.2%)
    2015-11-14T05:32:52.512+0000    imported 25359 documents

## Contando os restaurantes
    
    victorbzk(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
    25359