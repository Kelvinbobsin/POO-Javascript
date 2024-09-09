# Programação Orientada a objetos

Os quatro pilares da Programação Orientada a Objetos (POO) são princípios fundamentais que tornam esse paradigma poderoso e flexível. Vamos entender cada um deles em detalhes:

## 1. Abstração
A abstração é o processo de esconder detalhes complexos e mostrar apenas o que é essencial para o uso de um objeto. O foco está em definir o que um objeto faz, em vez de como ele faz isso. Isso ajuda a simplificar a complexidade e torna o código mais legível e fácil de manter.

### Exemplo:
Imagine que você tem um objeto Carro e ele tem métodos como acelerar(), frear(), e virar(). Como usuário, você não precisa saber como o motor ou a transmissão funcionam internamente para usar o carro. Você só precisa saber que chamar o método acelerar() faz o carro aumentar a velocidade.

class Carro {
  acelerar() {
    console.log("O carro está acelerando.");
  }

  frear() {
    console.log("O carro está freando.");
  }
}

const meuCarro = new Carro();
meuCarro.acelerar();  // Abstração em ação

## 2. Encapsulamento
O encapsulamento se refere à prática de esconder os detalhes internos de um objeto e proteger seus dados. Ele permite que os atributos de um objeto sejam acessíveis somente através de métodos definidos (getters e setters), mantendo a integridade e a segurança dos dados.

### Exemplo:
Você pode ter atributos privados que só podem ser modificados ou acessados por métodos públicos. Assim, você controla como os dados são alterados.

class ContaBancaria {
  constructor(saldoInicial) {
    let saldo = saldoInicial;  // Variável privada

    this.getSaldo = function() {
      return saldo;
    };

    this.depositar = function(valor) {
      if (valor > 0) {
        saldo += valor;
      }
    };
  }
}

const minhaConta = new ContaBancaria(100);
minhaConta.depositar(50);
console.log(minhaConta.getSaldo());  // Mostra 150

Nesse exemplo, o saldo da conta está encapsulado e só pode ser acessado pelos métodos getSaldo() e depositar().

## 3. Herança
A herança permite que uma classe derive de outra, herdando suas propriedades e métodos. Isso promove a reutilização de código e facilita a criação de hierarquias de classes.

### Exemplo:
Suponha que você tenha uma classe Animal e crie uma classe Cachorro que herda de Animal. O Cachorro vai herdar tudo que o Animal tem, mas pode também adicionar comportamentos específicos.

class Animal {
  constructor(nome) {
    this.nome = nome;
  }

  fazerSom() {
    console.log(`${this.nome} está fazendo um som.`);
  }
}

class Cachorro extends Animal {
  latir() {
    console.log(`${this.nome} está latindo.`);
  }
}

const cachorro = new Cachorro('Rex');
cachorro.fazerSom();  // Rex está fazendo um som.
cachorro.latir();     // Rex está latindo.

## 4. Polimorfismo
O polimorfismo permite que objetos de diferentes classes sejam tratados de maneira uniforme através de uma interface comum. Isso significa que diferentes classes podem ter métodos com o mesmo nome, mas comportamentos diferentes. O polimorfismo pode ser sobrecarga (mesmo método com diferentes assinaturas) ou sobrescrita (métodos com o mesmo nome em classes derivadas).

### Exemplo:
No exemplo a seguir, Cachorro e Gato herdam de Animal, mas sobrescrevem o método fazerSom() de maneiras diferentes.

class Animal {
  fazerSom() {
    console.log("O animal está fazendo um som.");
  }
}

class Cachorro extends Animal {
  fazerSom() {
    console.log("O cachorro está latindo.");
  }
}

class Gato extends Animal {
  fazerSom() {
    console.log("O gato está miando.");
  }
}

const animais = [new Cachorro(), new Gato()];

animais.forEach(animal => {
  animal.fazerSom();  // Polimorfismo em ação
});

Nesse caso, embora fazerSom() seja chamado para objetos diferentes (Cachorro e Gato), cada um se comporta de maneira única.

## Resumo dos 4 Pilares:
- Abstração: Mostra apenas o que é necessário, escondendo os detalhes complexos.
- Encapsulamento: Protege e oculta os dados internos do objeto, permitindo acesso controlado.
- Herança: Reutiliza código ao permitir que uma classe herde propriedades e métodos de outra.
- Polimorfismo: Permite que métodos tenham comportamentos diferentes em classes derivadas, mantendo uma interface comum.