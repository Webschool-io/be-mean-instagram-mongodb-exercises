# Artigo
**Autor**: Marcelo Santana Martins

**Prazo**: até dia 18 de Novembro de 2015

Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.


## Hoisting
*Hoisting* é o procedimento executado pelo JavaScript de "mover" a declaração de uma váriavel para o topo de seu escopo (quando está não for feita de forma explícita).

```
var idade; //declarada no escopo global

function exibeIdade(){    
    console.log(idade);
    var number = 27; //declarada no escopo de exibeIdade()
}

idade = 21;
exibeIdade();
```

No exemplo acima, será exibido *undefined* no console. Isso ocorre pois, como existe a declaração da variável idade dentro do escopo de `exibeIdade()` e ela se encontra no final, o próprio compilador se encarrega de declará-la no topo do escopo.

Com isso, o código ficaria da seguinte forma:

```
var idade;

function exibeIdade(){
    var number; //hoisting de number
    console.log(idade);
    number = 27;
}

idade = 21;
exibeIdade();
```



## Closure
É a forma de como uma função é definida dentro de outra função. Isso permite que a função utilize três tipos de variáveis: locais, da função pai e globais.

```
function adicionaValor(a) {
  return function(b) {
    return a + b;
  }
}

var contaCorrente = adicionaValor(20);
var saldo = contaCorrente(10); 
console.log(saldo);  // saldo é 30, pois o valor de contaCorrente iniciou com 20 e foi adicionado 10.
```

*Closures* podem ser utilizados em funções que são acionadas por usuários, e agindo como um *callback*.




## Variável Global
Variáveis globais são declaradas fora do escopo de uma função. Uma variável global pode ser acessada e ter seu valor alterado dentro de qualquer função.

A sintaxe para declaração é:
```
var cor = 'azul';

function exibeCor() {
	console.log(cor); //irá exibir o valor azul.
}
```




## Variável por parâmetro
Quando uma função recebe uma variável por parâmetro, ela será tratada como uma nova variável dentro do seu escopo.
```
function soma(a, b) {
	return a + b;
}

console.log(soma(3, 5));  //imprime o valor 8.
```

Caso seja utilizada uma variável global, além de poder acessar o seu valor, poderá alterá-lo.

```
var a = 2;
var b = 4;

function mudaValor(val){
  return (a = val);
};

console.log(mudaValor(b)); // imprime o valor 4 (além de retornar o valor de b, altera o valor de a com o mesmo valor);
console.log(a);            // imprime o valor 4.
```



## Instanciação usando uma IIFE
O termo IIFE significa `Immediately-Invoked Function Expression` e define uma função que é executada no momento da sua definição. Utilizamos quando queremos criar um escopo no JavaScript para que as variáveis definidas dentro da função não poluam o escopo global.

Uma variável pode receber um valor de uma IIFE da seguinte forma:

```
var contador = (function () { 
	var i = 1;

	return function () {		
		return i++;
	}
}());

console.log(contador()); //exibe o valor 1.
console.log(contador()); //exibe o valor 2.
console.log(contador()); //exibe o valor 3.
```

Para passar uma variável por parâmetro para uma IIFE, deve ser colocado na última abertura de parenteses da sintaxe abaixo:
```
(function (val) {
	console.log(val)
}('Passando parâmetros para uma IIFE'));
```