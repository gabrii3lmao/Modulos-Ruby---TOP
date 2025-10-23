Enumerables é um conjunto de métodos build-in que são incluídos tanto em arrays quanto em hashes. Enumerables foram projetados para fazer certos padrões de iteração de arrays e hashes muito, muito mais fáceis. 

Vamos dizer que você queira fazer uma festa com seus amigos, mas você não quer convidar um amigo em específico. Como você faria isso?
Provavelmente seria assim:
``` ruby
amigos = ["carlos", "andre", "lucas", "julia", "marcos", "vinicius"]
convidados = []
amigos.each do |amigo|
if amigo != "lucas"
convidados << amigo
end
end
convidados #=> ["carlos", "andre", "julia", "marcos", "vinicius"]
```

Se você não quiser ter que sempre reinventar a roda toda vez que for fazer uma festa, você pode usar o método `#select`:
``` ruby
amigos = ["carlos", "andre", "lucas", "julia", "marcos", "vinicius"]
amigos.select{|amigo| amigo != "lucas"}
#=> ["carlos", "andre", "julia", "marcos", "vinicius"]
```

Podemos ir ainda mais longe: 
``` ruby
amigos.reject{|amigo| amigo == "lucas"}
#=> ["carlos", "andre", "julia", "marcos", "vinicius"]
```
### Método each
O método each é como Chuck Norris: faz de tudo e mais um pouco.
Esse método cria um iterator que vai percorrer o array inteiro, e vai atribuir cada elemento ao iterador.
Ex: 
``` ruby
amigos = ["carlos", "andre", "lucas"]
amigos.each {|amigo| puts "Olá, #{amigo}!"}
#=> "olá, carlos!"
#=> "olá, andre!"
#=> "olá, lucas!"
```

Vamos analisar linha por linha do código
- `amigos` é o nosso array com os nomes dos nossos amigos.
- `.each` é o método enumerable que vai chamar cada elemento do array.
- `{|amigo| puts "Olá, #{amigo}!"}` é um bloco de código, e o código dentro desse bloco vai percorrer cada elemento do array. Se o nosso array tiver 5 elementos, ele vai percorrer esses 5 elementos executando o nosso código.

Se você tiver um código que não cabe em apenas uma linha, você pode usar `do... end`: 
``` ruby
numeros = [1, 3, 5, 7, 9]
numeros.each do |soma|
soma **= 2
puts soma
end
```

`#each` também funciona com hashes, porém com algumas coisinhas  a mais. Por padrão, cada iteração vai guardar tanto a chave quanto o seu valor no seu bloco, dependendo de como você declara: 
```ruby
minha_hash = {1 => "um", 2 => "dois"}

minha_hash.each{|chave, valor| puts "a chave #{chave} tem o valor #{valor}"}
#=> "a chave 1 tem o valor um"
#=> "a chave 2 tem o valor dois"
```

```ruby
minha_hash = {1 => "um", 2 => "dois"}

minha_hash.each{|par| puts "Minha hash: #{par}"}
#=> minha hash: [1, "um"]
#=> minha hash: [2, "dois"]
#=> {1 => "um", 2 => "dois"}
```

### Método `#each_with_index`
Esse método funciona igual o `#each`, com a diferença de que aceita duas Variáveis de bloco, ao invés de apenas uma. A primeira variável é o valor da variável, e a segunda é o seu index dentro do array. 
Ex: 
``` ruby
frutas = ["maçã", "banana", "pêra", "melancia", "kiwi", "tomate"]

frutas.each_with_index{|fruta, index| puts fruta if index.even?

#=> "maçã"
#=> "pêra"
#=> "kiwi"
#=> ["apple", "banana", "strawberry", "pineapple"]
```

Assim como o método `#each`,  ele também retorna o array original ao final.
### Método `#map`
O método `#map` itera sobre cada elemento do array, modificando esse elemento de acordo com o bloco de código que escrevermos, modificando o array original. Por exemplo:
``` ruby
amigos = ["carlos", "andre", "lucas"]
amigos.map{|amigo| amigo.upcase}
amigos
#=> ["CARLOS", "ANDRE", "LUCAS"]
```

Agora, vamos dizer que você fez o seu pedido em alguma lanchonete, mas queira mudar o tamanho da porção. Isso é possível com `#map` e `#gsub`. 
``` ruby
meu_pedido = ["batata frita pequeno", "refrigerante pequeno", "hamburguer pequeno"]

meu_pedido.map{|pedido| pedido.gsub{'pequeno', 'grande'}}
#=> "batata frita grande", "refrigerante grande", "hamburguer grande"
```

### Método `#select`
O método `#select` (ou `#filter`) passa uma condição dada para todo elemento de um array, e retorna apenas os elementos que atendem a essa condição.
``` ruby
boletos = [400, 500, 70, 50, 240]
boletos.select{|conta| conta < 100}
#=> [70, 50]
```

Se quisermos, também podemos usar esse método em um hash: 
``` ruby
boletos = {
"água": 70,
"luz": 50,
"streaming": 240,
"agiota": 500,
"lazer": 400
}

print boletos.select{|conta, valor| valor < 100}
#=> {água: 70, luz: 50}
```

outro exemplo: 
``` ruby
amigos = {
"carlos" => "sim",
"andre" => "sim",
"lucas" => "não",
"julia" => "não",
"marcos" => "sim",
"vinicius" => "não"
}
amigos.select{|nome, resposta| resposta == "sim"}
#=> {"carlos" => "sim, "andre" => "sim", "marcos" => "sim"}
```

### Método `#reduce`
A ideia geral do `#reduce` é que ele pegue todo o array e reduza ele a só um objeto. Você usa `#reduce` se quiser o output de um único valor.

Por exemplo, vamos dizer que você quer a soma de todos os elementos de um array:
``` ruby
numeros = [1, 2, 4, 8, 16]
numeros.reduce{|acumulador, atual| acumulador += atual}
#=> 21
```
o primeiro argumento do método `#reduce` é o acumulador. O resultado de cada operação é guardado dentro do acumulador, e então é passado para a próxima operação. O acumulador também é o resultado retornado pelo método `#reduce`, ao final da operação.

O método `#reduce` também pode ser usado para diversas outras coisas, como um sistema de contagem de votos: 
``` ruby
votos = ["lula", "bolsonaro", "lula", "lula", "lula", "bolsonaro", "lula", "lula"]
votos.reduce(Hash.new(0)) do |resultado, voto|
resultado[voto] += 1
resultado
end
```

### Métodos explosivos
Caso você seja esperto, talvez você tenha reparado que nenhum dos métodos anteriores modificou o array original. Isso acontece como uma forma de tentar evitar a perda de informações por descuido. 

Mas, caso você queira que alguns desses métodos mudem o array original, você pode usar as suas versões "explosivas" ou "extremas".
``` ruby
amigos = ["carlos", "andre", "lucas", "julia", "marcos", "vinicius"]

amigos.map!{ |amigo| amigo.upcase }
amigos #=> ["CARLOS", "ANDRE", "LUCAS", "JULIA", "MARCOS", "VINICIUS"]
```

Esses métodos explosivos são identificados pelo operador `!` que vem apos os seus nomes. Todos esses métodos são explosivos e modificam o array ou o hash original.

Geralmente, pelas boas práticas, nós não usamos esses métodos... Não usamos. Se lembre do psicopata que vai ler o seu código depois. Ele ainda sabe onde você mora.

Ir para o [[Ruby Cap1 Módulo 10. Métodos Enumeráveis de Predicado]]

