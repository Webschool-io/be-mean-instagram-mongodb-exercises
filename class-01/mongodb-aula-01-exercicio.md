# MongoDB - Aula 01 - Exercício
autor: Renato Ferreira

## Importando os restaurantes

.....

vagrant@vagrant-ubuntu-trusty-64:~$ mongoimport --db be-mean --collection restaurantes --file /vagrant/restaurantes.json 
2015-11-15T14:12:42.766+0000	connected to: localhost
2015-11-15T14:12:45.429+0000	imported 25359 documents

....

## Contando os restaurantes
> db.restaurantes.find({}).count()
25359
