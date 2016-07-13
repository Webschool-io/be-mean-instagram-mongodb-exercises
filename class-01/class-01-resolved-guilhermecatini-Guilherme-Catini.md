# MongoDB - Aula 01 - Exercício
autor: Guilherme Catini

## Importando os restaurantes

PS C:\Users\Guilherme> mongoimport.exe --db be-mean --coll
odb\material\restaurantes.json"
2016-07-12T20:46:56.914-0300    connected to: localhost
2016-07-12T20:46:56.927-0300    dropping: be-mean.restaura
2016-07-12T20:46:58.771-0300    imported 25359 documents

## Contanto os restaurantes
> db.restaurantes.find({}).count()
25359