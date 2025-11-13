A **Programação Orientada a Objetos (POO)** é um paradigma de programação que organiza o código em torno de **objetos** — entidades que combinam **dados (atributos)** e **comportamentos (métodos)**.

A ideia é pensar em **"coisas"** do mundo real: pessoas, carros, monstros de RPG... e traduzi-las em código.

### 🧩 Conceitos fundamentais

Os quatro pilares da POO são: 
- Abstração: 
  Simplificar a realidade complexa, representando apenas o que é essencial para o problema.
  Você não precisa modelar cad célula de uma pessoa - só o que for útil para o programa
- Encapsulamento
  Esconder os detalhes internos de uma classe e expor apenas o necessário. 
  Pense nisso como um painel de um carro: Você usa o volante e os pedais, mas não precisa ver o motor.
- Herança
  Permite criar novas classes baseadas em outras.
  A classe filha herda atributos e métodos da classe pai, podendo sobrescrevê-los quando quiser.
- Polimorfismo
  Permite que objetos diferentes respondam a uma mesma mensagem (método), mas de formas distintas.
  Um gato e um cachorro podem ter o método `falar`, mas um vai miar e o outro latir.
--- 
### 🧠 Abstração em Ruby
A abstração é o ato de modelar um conceito do mundo real em uma classe.
``` ruby
class Pessoa
	def initialize(nome, idade)
	@nome = nome
	@idade = idade
	end
end
```

Essa classe é um abstração de uma pessoa: guarda informações (nome e idade), mas não se preocupa com todos os detalhes biológicos, sociais ou existenciais.

---
### 🔒 Encapsulamento

Encapsulamento significa **proteger o estado interno de um objeto**. 
Em Ruby, fazemos isso através de métodos de acesso ou dos auxiliares
`attr_reader`, `attr_writter` e `attr_acessor`.
``` ruby
class ContaBancaria
	attr_reader :saldo
	
	def initialize
	@saldo = 0
	end
	
	def depositar(valor)
	@saldo += valor
	end
	
	def sacar(valor)
	@saldo -= valor if valor <= @saldo 
	end
end
```

Observe que o saldo não é alterado diretamente; só pode ser modificado pelos métodos `depositar` e `sacar`.

---
### 🧬 Herança
A herança permite reutilizar código entre classes relacionadas.
``` ruby
class Animal
	def falar
		"Som genérico"
	end
end

class Cachorro < Animal
	def falar
	"Au au!"
	end
end

class Gato < Animal
	def falar
		"Miau!"
	end
end
```

A classe `Cachorro` e `Gato` herdam de `Animal` e sobrescrevem o método `falar`.

--- 
### 🌀 Polimorfismo
O exemplo anterior já mostrou o polimorfismo em ação: 
Vários objetos respondem ao mesmo método (`falar`), mas o comportamento muda conforme o tipo do objeto.

Outro exemplo, mais "vida real":
``` ruby
class Pagamento
	def processar
		raise NotImplementedError, "Esse método deve          ser implementado pelas subclasses"
	end
end

class Pix < Pagamento
	def processar
		"processando pagamento via Pix..."
	end
end

class Cartao < Pagamento
	def processar
		"Processando pagamento via cartão..."
	end
end
```
O mesmo método `processar`, mas implementado de formas diferentes. 
Bem útil quando você quer expandir o sistema sem mexer no código que já existe - o sonho de todo desenvolvedor que tem medo de quebrar tudo.

---
### ⚙️ Construtor (`initialize`)

O construtor é o método especial chamado automaticamente quando um objeto é criado.
Em Ruby, esse método se chama `initialize`
``` ruby
class Pessoa
	def initialize(nome)
	  @nome = nome
	  puts "#{nome} foi criada!"
	end
end

Pessoa.new("Luisa")
#=> "Luisa foi criada!"
```

Se a classe herda de outra e você quer chamar o construtor do pai, use `super`
``` ruby
class Animal
	def initialize
	  puts "Um animal nasceu!"
	end
end

class Cachorro < Animal
  def initialize
    super
    puts "E é um cachorro!"
  end
end

Cachorro.new
# => "Um animal nasceu!"
# => "E é um cachorro!"
```

### 🧱 Objetos e Variáveis de Instância
Os objetos são as "coisas" que criamos a partir de classes.
As variáveis de instância (começam com `@`) guardam o estado interno do objeto.
``` ruby
class Pessoa
  def initialize(nome)
    @nome = nome
  end

  def nome
    @nome
  end
end

p1 = Pessoa.new("Ana")
p2 = Pessoa.new("Beatriz")

puts p1.nome  # => "Ana"
puts p2.nome  # => "Beatriz"
```
Cada instância tem seu próprio conjunto de dados - `p1` e `p2` não compartilham o mesmo `@nome`.

--- 
### 🔧 Métodos
Os métodos definem o comportamento dos objetos.
Eles são funções dentro de um classe, usados para manipular os dados internos.
``` ruby
class Retangulo
  def initialize(largura, altura)
    @largura = largura
    @altura = altura
  end

  def area
    @largura * @altura
  end
end

r = Retangulo.new(10, 5)
puts r.area  # => 50
```
Se quiser ser mais "rubystíco", pode usar `attr_reader` para evitar criar métodos só para leitura:
``` ruby
class Retangulo
  attr_reader :largura, :altura

  def initialize(largura, altura)
    @largura = largura
    @altura = altura
  end
end
```
 --- 
 A programação Orientada a Objetos serve para organizar o código de forma mais modular, legível e extensível.
 Em Ruby, ela é naturalmente integrada à linguagem - praticamente tudo é um objeto.

> "_Nem tudo precisa ser um objeto... mas quando for, faça direito".

Ir para o [[Ruby Cap2 Módulo 1. POO]]
