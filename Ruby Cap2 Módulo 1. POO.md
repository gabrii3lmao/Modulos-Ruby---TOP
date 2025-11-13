### Ruby - Classes e instâncias
**Conceito** 
- Classes organizam código e dados relacionados.
- Tudo em Ruby é um objeto, e todo objeto é uma instância de uma classe.
- Instâncias compartilham métodos, mas têm variáveis próprias.
---
### Criando classes
``` ruby
class Viking
	def initialize(nome, idade, vida, forca)
	@nome = nome
	@idade = idade
	@vida = vida
	@forca = forca
	end
end
```
- `::new` cria uma instância e chama `#initialize`
- Variáveis com @ são variáveis de instância, únicas por objeto.
---
### Acesso a Variáveis
``` ruby
attr_acessor :nome, :vida
```
- `attr_reader` => só leitura.
- `attr_writer` => só escrita.
- `attr_accessor` => ambos.
- Evite expor variáveis sem necessidade.
---
### Métodos

- Métodos definidos dentro da classe são de instância.
- Chamados em objetos: `oleg.attack(thor)`
- Use self para acessar métodos e atributos da própria instância.

⚠️ OBS:  Ruby às vezes precisa de `self.` para distinguir entre acessar e atribuir variáveis (`vida += 1` vs `self.vida += 1`).

--- 
### Métodos e Variáveis de Classe

``` ruby
@@total_vikings = 0

def self.criar_guerreiro(nome)
  Viking.new(nome, rand(80..120), rand(18..40), rand(5..10))
end
```

- Variáveis de classe usam `@@`
- Métodos de classe usam `self.` e não acessam variáveis de instância.
---
### Proteção de métodos e variáveis

**Regras básicas**
- Public (padrão): qualquer um pode chamar o método com qualquer receiver.
- Private: não permite receiver explícito - só pode ser chamado sem `obj.` dentro da própria instância. Usado para helpers internos.
- Protected: permite chamadas com receiver, mas apenas por instâncias da mesma classe ou subclasse. Útil quando objetos do mesmo tipo precisam acessar estado entre si (ex: comparar vida de dois Vikings). 

**Diferença prática:**
``` Ruby
class Pessoa
  def publico; end #publico
  
  protected
  def protegido; end # pode ser chamado por outro objeto pessoa ou subclass.
  
  private
  def privado; end # só `privado` (sem receiver) dentro da instância
end
```

Exemplo: 
- Quero expor leitura de `vida`, impedir alteração externa direta; só permitir que `take_damage` altere vida.
``` ruby
class Viking
  attr_reader :nome, :vida
  attr_accessor :idade
  
  def initialize(nome, vida, ataque, idade)
  @nome = nome
  @vida = vida
  @ataque = ataque
  @idade = idade
  end
  
  def atacar(outro)
  outro.take_damage(dano_aleatorio)
  end
  
  def take_damage(amount)
  @vida -= amount
  puts morrer if @vida <= 0
  end
  
  private
  
  def morrer
  @morto = true
  "Aqui jaz #{nome}"
  end
  
  protected
  
  def dano_aleatorio
   rand((@ataque * 0.8).. (@ataque * 1.2)).to_i
  end
end
```
* `vida` só tem getter (`attr_reader`) - ninguém fora pode escrever `viking.vida = ...`.
* `morrer` é `private`: é uma rotina interna; não faz sentido ser chamada com receiver

**Boas práticas**
- Prefira `attr_reader` e métodos controlados (`take_damage`, `heal`) para alterar estado.
- Use `private` para helpers que só fazem sentido dentro do objeto.
- Use `protected` quando duas instâncias do mesmo tipo precisarem acessar métodos entre si (comparações, duelos, etc).
- Evite expor setters públicos sem motivo - facilita bugs e testes ruins.
---
### Herança

``` ruby
class Viking < Pessoa
  def initialize(nome, vida, ataque, idade, arma)
  super(nome, vida, ataque, idade)
  @arma = arma
  end

end
```
- `Viking` herda métodos e variáveis de `Pessoa`
- Use `super` para chamar o método da classe-pai
- Classes podem sobrescrever métodos do pai.
--- 
### Constantes
- Escritas em maiúsculas (`MAX_HEALTH = 120`).
- Use para valores que não mudam.
- Diferem de variáveis de classe porque são imutáveis por  convenção.
--- 
### Resumo rápido
- Use classes para representar entidades com dados e comportamento
- Use instâncias para objetos individuais.
- `attr_*` facilita acesso a variáveis.
- `super` e herança evitam repetições
- Constantes => valores fixos.
- Métodos de classe => utilitários ou fábricas (`create_warror`).


Ir para o [[Ruby Cap2 Módulo 2. Gerenciamento de projeto]]