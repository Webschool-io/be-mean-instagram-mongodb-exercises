# MongoDB - Aula 01 - Exercício
Áutor: Hélio Marcondes

## Importando os restaurantes
```
./mongoimport.exe --db be-mean --collection restaurantes --drop --file C:\\Users\\HELIO\\Downloads\\restaurantes.json
2016-01-25T22:15:37.145-0200    connected to: localhost
2016-01-25T22:15:37.146-0200    dropping: be-mean.restaurantes
2016-01-25T22:15:39.097-0200    imported 25359 documents

```
## Contando os restaurantes
```
db.restaurantes.find({}).count();
25359
X
```