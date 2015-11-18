# Instanciação de variáveis no Javascript
**autor**: José Antonio Gaeta Mendes

**Prazo**: até dia 18 de Novembro de 2015

Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.

## Hoisting

Hoisting nada mais é do que o mecanismo usado por JavaScript para definir o escopo de variáveis e funções. Todavia, seu comportamento costuma confundir o iniciante, tornando-se essencial o perfeito entendimento do seu funcionamento para utilizar plenamente este que é um dos aspectos mais expressivos e poderosos da linguagem.

A palavra Hoist, em inglês, significa "elevar, alçar, erguer", no sentido, por exemplo, de um guindaste no porto que suspende a carga. Em JavaScript, o sentido é de "elevar" o escopo da variável ou função.

Diferentemente das linguagens que seguem o estilo de C, onde o escopo é definido a nível de bloco, em JavaScript, o escopo é definido a nível de função... e é daí que vem toda a confusão.

Vamos destrinchar isso com alguns exemplos. Examine o código a seguir:

```
var x = 1;
console.log(x); // 1
if (true) {
	var x = 2;
	console.log(x); // 2
}
console.log(x); // 2
```

Conforme indicado, as saídas no console serão 1, 2 e 2. Ou seja, o bloco **if** não criou uma variável local. Isso porque em JavaScript, apenas funções criam um novo escopo.

Um código equivalente em C, geraria a saída 1, 2 e 1. Deu para perceber a intrigante diferença?

Bom, e como é que ocorre o tal do *hoisting*? Se tentarmos executar o código a seguir, obteremos evidentemente uma mensagem de erro, uma vez que a variável `a` não está definida:

```
try {
  console.log(a)
} catch (e) {
  console.error('Variável não definida.')
}
```

Todavia, se mudarmos o código para:

```
try {
  console.log(a)
  var a = 2
} catch (e) {
  console.error('Variável não definida.')
}
```

inobstante a variável tenha sido declarada e inicializada depois da chamada de `console.log(a)`, obteremos o valor `undefined`, ao invés da mensagem de erro, porque ocorreu o **hoisting** da variável. Observe, por oportuno, que o *hoisting* é apenas da declaração, sem alcançar o valor inicializado.

Já com relação às funções, o comportamento do *hoisting* é um pouquinho diferente. Tanto o nome como o corpo da função são "elevados". Vamos analisar um exemplo bem curioso:

```
function foo(){
  function bar() {
    return 3
  }

  return bar()

  function bar() {
    return 8
  }
}

console.log(foo())
```

Quem disse que a saída no console será **8**, entendeu direitinho o funcionamento do **hoisting**!!! Vamos esmiuçar para aqueles que ficaram em dúvida.

No escopo da função `foo`, temos a primeira função `bar`, que já está no topo. Acontece que, depois do `return`, temos uma segunda função `bar` que é elevada pelo _hoisting_ e, como tem o mesmo nome, sobrescreve a primeira, retornando **8**. Bem simples depois de explicado, não é mesmo?

## Closure

Por definição, uma **closure**, que significa "fechamento" em português, é uma função que se refere a variáveis livres, ou independentes.

Consideremos a seguinte função:

```
function primeiroTrago() {
  var nome = "Nêga Fulô";
  function mostraNome() {
    alert(nome);
  }
  mostraNome();
}
primeiroTrago();
```

Nossa função `primeiroTrago` cria uma variável local chamada `nome` e define a função `mostraNome`, que é uma função aninhada (ou seja, um *closure*) -- está definida dentro da função primeiroTrago(), e está disponível apenas dentro do corpo daquela função. Observem que a função `mostraNome` não possui nenhuma variável local própria, utilizando-se da variável declarada na função ancestral.

Para concluir teoria das **Closures**, vamos fazer uma pequena modificação no nosso exemplo anterior:

```
function preparaTrago() {
  var nome = "Nêga Fulô";
  function mostraNome() {
    alert(nome);
  }
  return mostraNome;
}

var meuTrago = preparaTrago();
meuTrago();
```

Neste caso, a função `meuTrago` tornou-se uma **closure**, combinando duas coisas: a função propriamente dita, e o ambiente em que ela foi criada e esse ambiente incorpora todas as variáveis existentes no momento em que a função foi criada. É por isso que `meuTrago` contém a variável com a excelente cachaça "Nêga Fulô", existente quando de sua criação.

Na prática, o uso de **closures** é muito comum na programação de *front-end*. No código abaixo, usamos uma *closure* para redimensionar o texto de uma página **html**, de uma forma bem simples:

**arquivo html**
```
    <p>Um parágrafo de texto</p>
    <h1>um cabeçalho 1</h1>
    <h2>um cabeçalho 2</h2>

    <a href="#" id="tamanho-12">12</a>
    <a href="#" id="tamanho-14">14</a>
    <a href="#" id="tamanho-16">16</a>
```

**arquivo css**
```
body {
  font-family: Helvetica, Arial, sans-serif;
  font-size: 12px;
}

h1 {
  font-size: 1.5em;
}
h2 {
  font-size: 1.2em;
}
```

**código JavaScript**
```
function ajustaTamanho(tamanho) {
  return function() {
    document.body.style.fontSize = tamanho + 'px';
  };
}

var tamanho12 = ajustaTamanho(12);
var tamanho14 = ajustaTamanho(14);
var tamanho16 = ajustaTamanho(16);

document.getElementById('tamanho-12').onclick = tamanho12;
document.getElementById('tamanho-14').onclick = tamanho14;
document.getElementById('tamanho-16').onclick = tamanho16;
```


## Variável Global

Em JavaScript, uma variável tem escopo global quando é definida fora do escopo de uma função, podendo então ser referenciada em qualquer local dentro do documento corrente, como no seguinte exemplo:

```
var benssa = "Saravá!";

function foo() {
    benssa = "Saravá, meu pai!";
    console.log(benssa);
}

console.log(benssa);
foo();
console.log(benssa); // benssa foi sobrescrita por foo()
```

Em JavaScript, caso seja atribuído um valor a uma variável local **antes** de que ela tenha sido declarada com a palavra-reservada `var`, ela se tornará **global**. Portanto, muita atenção! Para evitar problemas, a declaração de variáveis usando explicitamente `var` é considerada uma boa prática a ser seguida.

## Variável por parâmetro

As variáveis passadas por parâmetro para as funções são utilizadas em variáveis de escopo local pelas mesmas.

A princípio, parece não ter muita lógica passar uma variável global como argumento para a função, pois, sendo global, ela já pode acessá-la. Na verdade, contudo, há um caso bem específico em que se passa uma variável global como parâmetro para uma função: é quando aquela função retornará outra função que captura o valor corrente daquela variável, ou seja o caso das **closures** que vimos acima. Vejamos um exemplo:

```
function constroiFnOla (nome) { 
  return( function () { console.log( "Olá " + nome + "!" ) } );
}

alcunha = "Zé do Caixão";
olaZe = constroiFnOla(alcunha); // variável global passada como parâmetro

alcunha = "Maria Gasolina";
olaMaria = constroiFnOla(alcunha); // variável global passada como parâmetro

olaZe(); // exibe: "Olá Zé do Caixão!"
helloJudy(); // exibe "Olá Maria Gasolina!"
```


## Instanciação usando uma IIFE

Antigamente, as funções executadas no mesmo momento em que são definidas eram chamadas "self-executing anonymous function", isto é, "função anônima auto-executável". Num artigo publicado em 2010, um sujeito chamado [Ben Alman](https://github.com/cowboy), escreveu um artigo propondo denominar essas funções de "Immediately-Invoked Function Expression (IIFE)", que se traduz em português como "Definição de Função Imediatamente Executável".

As IIFE são muito usadas em JavaScript funcional e o seu "jeitão" é o seguinte:

`(function(){})();`

```
var concatenador = (function() {
   var minhaFrase = "";
   return function(x) { 
   return minhaFrase = 
   !!minhaFrase ? minhaFrase.concat(" ", x) : minhaFrase.concat(x);
 }
})();
  
concatenador("Olá"); // "Olá"
concatenador("Mundo!"); // "Olá Mundo"
  
minhaFrase; // minhaFrase não está definida
```

Aqui a IIFE retorna outra função para a concatenação da `string` da variável `minhaFrase`. Uma coisa bastante interessante é que `minhaFrase` limita-se ao escopo da IIFE, e seu acesso direto não é permitido em nenhuma hipótese.
