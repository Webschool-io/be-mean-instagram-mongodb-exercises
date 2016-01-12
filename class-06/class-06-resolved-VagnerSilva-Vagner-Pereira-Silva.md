# MongoDB - Aula 06 - Exercício
autor: Vagner Pereira Silva

## 1. Realizando a query pelo name sem index

```js
> db.pokemons.find({name: /squirtle/i}).explain('executionStats').executionStats.executionStages.docsExamined
620

```

## 2. Realizando a query pelo name com index criado

```js

> db.pokemons.find({name: /squirtle/i}).explain('executionStats').executionStats.executionStages.docsExamined
0

```


## 3. Realizando a query com dois campos juntos sem o index criado

```js

> db.pokemons.find({name: /squirtle/i, types: /fire/i}).explain('executionStats').executionStats.executionStages.docsExamined
620

```

## 4. Realizando a query com dois campos juntos e com os dois indexes

```js

> db.pokemons.find({name: /squirtle/i, types: /fire/i}).explain('executionStats').executionStats.executionStages.inputStage.docsExamined
1

```
