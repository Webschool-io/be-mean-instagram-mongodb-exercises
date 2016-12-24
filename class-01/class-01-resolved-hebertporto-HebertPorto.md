
# MongoDb - Aula 01 - Exercício Resolvido - Hebert Porto
Autor: Hebert Porto

## 1 - Importando base de dados

```
vagrant@vagrant-ubuntu-trusty-64:/vagrant/node_apps/be-mean-instagram/Apostila/module-mongodb/src/data$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --
drop --file restaurantes.json
connected to: 127.0.0.1
Tue Feb  9 17:14:55.231 dropping: be-mean.restaurantes
Tue Feb  9 17:14:56.948 check 9 25359
Tue Feb  9 17:14:56.953 imported 25359 objects
```

## 2 - Listando base de dados

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
25359
```