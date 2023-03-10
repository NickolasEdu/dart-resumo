# Index

## Parte 1 - Conceitos
- [Introdução](#dart)
- [Operadores](#operadores)
- [Tipos de Dados](#tipos-de-dados)
- [Métodos](#métodos)
- [Variáveis](#variáveis)
- [Conjuntos](#conjuntos)
- [Condicionais](#condicionais)
- [Laços de Repetição](#loops)
- [Funções](#funções)

## Parte 2 - Introdução a Programação Orientada a Objetos (POO)
- [POO](#oop---object-oriented-programming)
- [Classes Abstratas](#classes-abstratas)
- [Mixins](#mixins)


# Parte 1 - Conceitos

## Dart
Dart é uma linguagem de programação desenvolvida pela Google, lançada em 2011. É uma linguagem orientada a objetos e projetada para ser rápida, escalável e fácil de aprender. Ela é usada para desenvolver aplicativos para a web, dispositivos móveis, desktop e até mesmo para o desenvolvimento de servidores.

Dart é frequentemente usado em conjunto com o Flutter, um framework de desenvolvimento de aplicativos móveis que usa Dart como linguagem de programação. Isso se deve em parte à excelente integração do Dart com o Flutter, tornando-o uma escolha popular para desenvolvedores que desejam criar aplicativos móveis modernos e eficientes.

## Operadores

De comparação

| Operador | Descrição |
| --- | --- |
| >= | Maior ou igual |
| > | Maior |
| <= | Menor ou igual |
| < | Menor |
| is | É do mesmo tipo |
| is! | Não é do mesmo tipo |
| == | Igual |
| != | Diferente |
| && | E lógico (AND) |
| || | OU lógico (OR) |

[Voltar ao índice](#index)

## Tipos de dados

O dart tem o comportamento do fato de ser uma linguagem fortemente tipada, e a declaração destes tipos tem influência na declaração de variáveis, sendo assim uma vez que atribuímos um valor a uma variável, valores de outros tipos não poderão ser armazenados por essa mesma variável

A declaração de variável simples é feita a partir de: 

tipo do dado > nome que o valor será atribuído > valor

*Ao declarar o tipo do dado pode se deixar um sinal de ‘?’ no qual indica que esse valor pode ser nulo, o que não irá acarretar um problema no interpretador de código.*

```dart
// Número que pode receber nulo
int? idade = 18;

// Declaração de número quebrado - decimal
double altura = 1.70;

// Declarção com string
String texto = "Isso é uma string?";

// Valores boleanos
bool boleano = true;

print("$texto, $boleano. Minha idade é: $idade e tenho $altura metros de altura.");
```

Esse comportamento padrão das declarações de dados pode ser alterado quando usamos o valor dinâmico, como o nome já diz é uma declaração que permite uma substituição de tipos de dados a variáveis.

```dart
dynamic idade = 22;
print(idade);

idade = "22 anos";
print(idade);
```

[Voltar ao índice](#index)

## Métodos

Métodos de transformação com tipo numérico.

| Método | Descrição |
| --- | --- |
| abs() | Retorna o valor absoluto do número. |
| ceil() | Retorna o último inteiro imediatamente superior. |
| ceilToDouble() | Retorna o último número imediatamente superior com o tipo double. |
| clamp(num limiteInferior, num limiteSuperior) | Se o número estiver dentro do limite, retorna o número. Se não, retorna o limite o qual ele extrapolou. |
| compareTo(num outro) | Compara com outro número, retornando 1 quando forem diferentes e 0 quando forem iguais. |
| floor() | Arredonda o número para o inteiro anterior. |
| floorToDouble() | Arredonda o número para o número inteiro anterior no tipo double. |
| remainder(num outro) | Retorna a sobra da divisão com outro número. |
| round() | Arredonda o número para o inteiro mais próximo. |
| roundToDouble() | Arredonda o número para o valor inteiro mais próximo no tipo double. |
| toDouble() | Converte o número para Double. |
| toInt() | Converte o número para Int. |
| toString() | Converte o número em uma String. |
| toStringAsExponential([int digitos]) | Converte para string com exponencial. |
| toStringAsFixed(int decimais) | Converte para String contendo N casas decimais. |
| toStringAsPrecision(int digitos) | Converte para String contendo N dígitos. |
| truncate() | Retira as casas decimais, retornando um inteiro. |
| truncateToDouble() | Retira as casas decimais, retornando um double. |

[Voltar ao índice](#index)

## Variáveis

Anteriormente vimos os tipos de dados que podem ser atribuídos as variáveis, agora veremos a declaração de variáveis a partir de palavras chave. Nesta declaração nós não indicamos qual o tipo do valor, ele será atribuído pelo interpretador de código.

Para verificar qual é o tipo atribuído, vamos usar o método ‘runtimeType’, que retorna o tipo do valor de um objeto.

Exemplo:

```dart
/* 
* A primeira variável está declarada como int (de inteiro)
* enquanto a segunda foi declarado um número inteiro, mas a atribuição do tipo
* foi feita pelo próprio interpretador;
*/

	int number = 1;
  print(number.runtimeType); // int
  
  var variavel = 1;
  print(variavel.runtimeType); // int
```

Um ponto importante é que variáveis declaradas como var podem receber novos valores, desde que sejam do mesmo tipo em que foi atribuído inicialmente.

```dart
var nome = "Joao";
  print(nome); // Joao
  
  nome = "João";
  print(nome); // João
  
  nome = 1;
  print(nome); // Error: value of type 'int' can't be assigned to a variable of type 'String'
```

### Final x Const

São variáveis que não permitem a alteração, onde o valor atribuído não poderá mais ser mudado. A diferença está **`final`** é avaliado em tempo de execução, enquanto **`const`** é avaliado em tempo de compilação.

Na prática podemos declarar a existência de uma variável definida com **`final` pode receber um valor em outra linha de código, enquanto o mesmo não ocorre na utilização de `const`.**

```dart
// Declaração e output de final
final var1;
var1 = "Valor da final";

print(var1); // Valor da variável

// Declaração e output de const
const var2;
var2 = "Valor de const";

print(var2); // Error: The const variable 'var2' must be initialized.
```

[Voltar ao índice](#index)

## Conjuntos

São coleções que agrupam dados - assim como arrays em Javascript.

********LIST:********

É uma coleção ordenada e mutável de elementos. É possível adicionar, remover ou atualizar elementos em uma lista, sendo que a indexação é como na maioria das linguagens, o primeiro elemento parte da posição zero.

Listas são declaradas com o uso de ‘[ ]’

Uma particularidade nesse caso ( em comparação a JS e Python) é que assim como as variáveis, as listas também devem ser declaradas com o tipo de dado que será recebido, porém também podemos declarar e armazenar listas em variáveis.

```dart
List<String> frutas = ['maçã', 'banana', 'laranja'];
print(frutas); // [maçã, banana, laranja]

// Imprimindo uma posição especifica da lista
var carros = ['Honda', 'Mercedez', 'BMW'];
print(carros[2]); // BMW

// Adicionando mais um valor
carros[3] = 'Jeep';
print(carros);
```

**********SET:**********

Uma coleção não ordenada e sem duplicatas de elementos. Diferentes das listas o Set agrupa os valores com ‘{ }’, e o acesso aos seus elementos pelo index deve ser feito pelo método ‘elementAt’

```dart
Set<int> numeros = {1, 2, 3, 4, 5};
print(numeros); // {1, 2, 3, 4, 5}

// adicionando um novo valor
numeros.add(6);
print(numeros); // // {1, 2, 3, 4, 5, 6}

// Set atribuído a uma variavel
var ids = {1, 2, 3, 4, 5};
print(ids); // {1, 2, 3, 4, 5}

// Imprimindo o valor pelo seu index
print(ids.elementAt(2)); // 3
```

********MAP:********

Uma coleção de pares chave-valor, onde cada chave deve ser única. O conjunto é feito dentro de ‘{ }’ e seu acesso através das chaves que recebem um valor.

```dart
// Declarando sem especificar o tipo de dado
var mapCol = {
    'nome' : 'João',
    'senha' : '1234',
    'id' : 9952,
  };
print(mapCol); // {nome: João, senha: 1234, id: 9952}

// Declarando os tipos de <Chave, valor>
Map<String, int> idades = {'João': 25, 'Maria': 30, 'Pedro': 20};
print(idades); // {João: 25, Maria: 30, Pedro: 20}

// Acessando um valor através de sua chave
print(idades['Pedro']); // 20
```

*Dart também possui outras coleções como filas, pilhas e árvores*

[Voltar ao índice](#index)

## Condicionais

As condicionais são utilizadas para permitir que o código execute diferentes caminhos de acordo com uma condição específica. Existem duas estruturas principais de condicionais em Dart: **`if-else`**
 e **`switch-case`**. Exemplos:

**************IF ELSE**************

A estrutura **`if-else`**permite executar um determinado bloco de código se uma condição for verdadeira, caso não seja é passado para a próxima condição até encontrar uma que seja satisfeita.

```dart
int idadeMin = 18;
String info = "";
	
	if(idadeMin >= 18){
		info = "Acesso permitido";
	} else {
		info = "Acesso negado";
	};
  
  print(info);
```

O if-else também pode ser simplificado, como if ternário:

```dart
int idadeMin = 18;
String info = "";
	
info = idadeMin >= 18 ? "Aprovado" :  "Reprovado";
  
print(info);
```

### Switch Case

A estrutura **`switch-case`** permite executar um bloco de código diferente para cada caso possível de um valor. Além de que podemos definir um padrão de respotas, para caso nenhum caso possível seja encontrado.

```dart
String language = "Dart";

switch(language){
	case "Dart":
		print('A linguagem é Dart');
		break;
	case "Javascript":
		print('A linguagem é Javascript');
		break;
	case "Python":
		print('A linguagem é Python');
		break;
	default:
		print('Error 404, nenhuma linguagem encontrada');
		break;
}
```

[Voltar ao índice](#index)

## Loops

Em Dart, existem três estruturas principais de repetição: **`while`**, **`do-while`**
 e **`for`.** Basicamente os loops são blocos de código que repetem uma ação durante um laço de repetição determinado.

**FOR**

A estrutura **`for`**executa um bloco de código um número específico de vezes

```dart
// Nesse caso enquanto o i for menor que 10, o laço se repetirá
for(int i = 0; 1 < 10; i++){
	print(i);
}
```

******************************WHILE & DO WHILE******************************

A estrutura **`while`**executa um bloco de código enquanto uma condição for verdadeira. Já o **`do-while`**executa um bloco de código pelo menos uma vez e, em seguida, continua a executá-lo enquanto uma condição for verdadeira.

```dart
// While - enquanto o j for menor que 10 continuará sendo executado
int j = 0;
while(j < 10){
	print(j);
	j++
}

// Do While - Faça K + 1, enquanto K for menor que 10
int k = 0;
do{
	print(k);
	k++;
} while(k < 10);

```

[Voltar ao índice](#index)

## Funções

Funções

Funções são blocos de código que podem ser chamados várias vezes em diferentes partes de um programa. Elas são usadas para executar ações e rotinas determinadas e podem receber argumentos para retornar valores.

Podemos dizer que em Dart há dois tipos de funções, as de retorno e as que apenas executam uma rotina, as funções que tem como objetivo retornar algo, devem assim como nas variáveis, receber uma indicação de qual o tipo esperado, enquanto a função de execução é chamada de `void`

```dart
// Toda ação nesta função será alto executada
void sayHello() {
  print('Hello world'); // Hello world
}
```

As funções que retornam algo devem receber o tipo de dado e são executadas na função `void`. Por serem funções que retornam valores, elas de certa forma funcionam como variáveis que serão lidas pela função de execução.

```dart
void main() {
  print(getGreeting());
  
  print(sum(2, 3));
}

String getGreeting() {
  return 'Olá, mundo!';
}

int sum(int a, int b) {
  return a + b;
}

// Olá, mundo!
// 5
```

[Voltar ao índice](#index)

# Parte 2 - Introdução a Programação Orientada a Objetos (POO)

## OOP - Object Oriented Programming

A Programação Orientada a Objetos (POO) é um paradigma de programação que se concentra em modelar o mundo real em termos de objetos, onde o programa é dividido em classes, que são templates ou modelos para a criação de objetos. Cada objeto é uma instância de uma classe, que contém atributos (variáveis que armazenam dados) e métodos (funções que executam operações) que definem o comportamento do objeto.

Os conceitos mais importantes do paradigma OOP são: `Classes, Atributos, métodos, objetos, construtores` além de `getters e setters`.  Vejamos os exemplos nos seguintes códigos e sua legenda.

```dart
// Declarando uma classe chamada conta bancária
class ContaBancaria {

	// Atributos da classe
  String numeroConta;
  String nomeTitular;
  double saldo;

	// Construtor
  ContaBancaria(this.numeroConta, this.nomeTitular, this.saldo);

	// Métodos da classe que são funções onde serão executadas ações dentro da classe
	// os quatro métodos declarados são: Depositar, Sacar, Verificar saldo e Transferir;
  void depositar(double valor) {
    saldo += valor;
    print('Depósito de R\$ ${valor.toStringAsFixed(2)} realizado.');
  }

  bool sacar(double valor) {
    if (saldo >= valor) {
      saldo -= valor;
      print('Saque de R\$ ${valor.toStringAsFixed(2)} realizado.');
      return true;
    } else {
      print('Saldo insuficiente.');
      return false;
    }
  }

  void transferir(double valor, ContaBancaria contaDestino) {
    if (sacar(valor)) {
      contaDestino.depositar(valor);
      print('Transferência de R\$ ${valor.toStringAsFixed(2)} realizada.');
    } else {
      print('Transferência não realizada.');
    }
  }
  
  double getSaldo() {
    return saldo;
  }
}
```

A partir disso é criado um objeto - também chamado de instância - onde receberá os valores referentes aos atributos definidos. Esses atributos funcionam como variáveis que armazenam e passam essa informação entre as funções.

```dart
void main() {
	
	// Instâncias da classe
  ContaBancaria conta1 = ContaBancaria('12345', "João", 1000.0); 
  ContaBancaria conta2 = ContaBancaria('67890', "Maria", 500.0); 

	// Execução de métodos
  conta1.transferir(500.0, conta2);
  double saldoAtual = conta1.getSaldo();
  print('O saldo atual da conta 1 é: R\$ ${saldoAtual.toStringAsFixed(2)}');

  saldoAtual = conta2.getSaldo();
  print('O saldo atual da conta 2 é: R\$ ${saldoAtual.toStringAsFixed(2)}');

	/* Outputs do código:
		Saque de R$ 500.00 realizado.
		Depósito de R$ 500.00 realizado.
		Transferência de R$ 500.00 realizada.
		O saldo atual da conta 1 é: R$ 500.00
		O saldo atual da conta 2 é: R$ 1000.00
	*/
}
```

LEGENDA:

Neste exemplo, a classe **`ContaBancaria`** contém três atributos: **`numeroConta`**, **`nomeTitular`** e **`saldo`**. Ela também possui um construtor que recebe os valores iniciais para esses atributos.

A classe também contém três métodos: **`depositar`**, **`sacar`**, **`transferir` e `verificar o saldo`**. O método **`depositar`** adiciona um valor ao saldo da conta, o método **`sacar`** subtrai um valor do saldo da conta (se houver saldo suficiente) e o método **`transferir`** transfere um valor da conta atual para outra conta de destino (se houver saldo suficiente).

### Atributos privados

Os atributos privados não podem ser acessados ou modificados por algo que esteja fora da classe aonde foram definidos. O uso dessa prática ajuda a proteger a integridade dos dados em uma classe e a evitar que objetos externos acessem ou modifiquem dados de maneira inadequada.

Em Dart, um atributo privado é definido usando o símbolo underscore (_) antes do nome do atributo. E a maneira de acessar e alterar seus valores vem a partir dos: `getters`e `setters`.

```dart
class Pessoa {
	
	// Atributos privados
  String _nome;
  int _idade;

		
	// Dois exemplos contendo Getter e Setter;
	/* 
		Primeiro o get associa o atributo a uma variável mutável
		essa variável recebe o valor da instância da classe
		E então é declarado pelo Setter
	*/
  String get nome => _nome;
  set nome(String nome) => _nome = nome;

  int get idade => _idade;
  set idade(int idade) => _idade = idade;
}

void main() {
  Pessoa pessoa = Pessoa();

  pessoa.nome = 'João';
  pessoa.idade = 25;

  print('Nome: ${pessoa.nome}');
  print('Idade: ${pessoa.idade}');
}
```

[Voltar ao índice](#index)

### Classes abstratas

Para declarar uma classe abstrata em Dart, utilizamos a palavra-chave **`abstract`**antes da palavra **`class`**. Essas classes recebem atributos que não são diretamente declarados, as instâncias serão definidas pelas classes que estendem a classe abstrata.

```dart
// Classe abstrata Pessoa
abstract class Pessoa {
  String nome;
  int idade;

  // Método abstrato
  void saudacao();

  // Construtor da classe Pessoa
  Pessoa(this.nome, this.idade);
}

// Classe Aluno que herda de Pessoa
class Aluno extends Pessoa {
  String curso;

  // Construtor da classe Aluno : referência a superclass
  Aluno(String nome, int idade, this.curso) : super(nome, idade);

  // Implementação do método abstrato da classe Pessoa
  void saudacao() {
    print("Olá, me chamo $nome e estou estudando $curso!");
  }
}

// Classe Professor que herda de Pessoa
class Professor extends Pessoa {
  String disciplina;

  // Construtor da classe Professor
  Professor(String nome, int idade, this.disciplina) : super(nome, idade);

  // Implementação do método abstrato da classe Pessoa
  void saudacao() {
    print("Olá, me chamo $nome e leciono a disciplina de $disciplina!");
  }
}

// Função principal
void main() {
  // Criação de instâncias das classes
  Aluno aluno1 = Aluno("João", 20, "Programação");
  Professor professor1 = Professor("Maria", 30, "Matemática");

  // Chamada dos métodos
  aluno1.saudacao(); // Olá, me chamo João e estou estudando Programação
  professor1.saudacao(); // Olá, me chamo Maria e leciono a disciplina de Matemática!
}
```

Atributos e métodos abstratos são declarados e não instanciados diretamente, isso será feito junto a definição da classe.

A palavra reservada `super` no construtor se refere a ‘superclass’ que no caso é a classe pai da função atual, sendo ela a classe que está se estendendo. 

Esses atributos passados de classe-pai para classe-comum é chamado de `herança`.

[Voltar ao índice](#index)

### Mixins

Em Dart, mixin é uma forma de compartilhar código entre classes sem usar herança. A diferença entre uma classe normal e um mixin é que um mixin não pode ser instanciado diretamente. Ele é projetado para ser mesclado em outras classes para compartilhar seu comportamento e atributos..

Os mixins são úteis para adicionar funcionalidades comuns a várias classes, sem precisar criar uma hierarquia de classes. Esse compartilhamento é feito a partir da palavra reservada `with`, que no caso funciona como classe-pai.

```dart
// Definir uma classe mixin chamada "Logger"
mixin Logger {
  
  // Método para imprimir uma mensagem de log
  void log(String message) {
    print('$runtimeType: $message');
  }
}

// Classe que usa o mixin Logger
class MyClass with Logger {
  void doSomething() {
    // Usando o método log definido no mixin Logger
    log('Hello World');
  }
}

void main() {
  
  // Criar uma instância de MyClass
  var obj = MyClass();

  // Chamar o método doSomething, que por sua vez chama o método log definido no mixin Logger
  obj.doSomething();
}
```

[Voltar ao índice](#index)