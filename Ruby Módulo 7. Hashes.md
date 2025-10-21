O Hash é um tipo de dado que armazena os valores de forma mais complexa em Ruby, bem similar aos objetos em Javascript.

### Arrays vs hashes
Para organizar os arrays, nomeamos os elementos dele de índices. Logo, se quiséssemos um determinado item desse array, precisaríamos saber em qual posição do array ele se encontra.

Mas com hashes é diferente. Podemos simplesmente chamar o nome do item que instantaneamente o hash retorna o valor dele para nós.

Pense como se os arrays fossem uma máquina de refrigerantes, onde você precisa informar a localização do refri que você quer, enquanto o hash é um restaurante, onde basta pedir o item.
### Criando hashes
Para criar um hash, o método mais comum é criando da forma literal usando chaves:
```ruby
my_hash = {
"uma palavra aleatoria" => "Aoba",
"neymar" => "traição",
"Nota em matemática" => 4.5,
"um array" => [1, 2, 3],
"um hash dentro de outro hash" => {}
}
```

Perceba que cada **par chave-valor** do hash, separados por vírgula, apontam para um valor. Por exemplo, a chave `"neymar"` aponta para o valor `"traição"`. Para isso usamos o operador _hash rocket_ `=>`.
### Acessando valores
Você pode acessar os elementos dentro de uma hash da mesma forma que acessa em arrays. usando os colchetes `[]`, junto com o item que você quer:
```ruby
calçados = {
   "academia" => "tênis",
   "escola" => "sapato",
   "casa" => "chinelos"
}

calçados["casa"]    #=> "chinelos"
```

Se você tenta acessar um hash com uma **chave** que não existe, o valor retornado será `nil`.  
Hashes também tem o método `#fetch`, que retornará um erro caso a **chave** não seja encontrada:
```ruby
calçados.fetch("festa") #=> KeyError: key not found: "festa"
```

Você também pode adicionar um valor padrão em vez de retornar um erro:
```ruby
calçados.fetch("festa", "sapato") #=> "sapato"
```
### Adicionando e mudando valores
Você pode adicionar um elemento ao hash chamando o elemento, e atribuindo um valor à ele:
```ruby
calçados["praia"] = "havaianas"
calçados #=> {"academia"=>"tênis","escola"=>"sapato","casa"=> "chinelos", "praia" => "havaianas"}
```

Você pode fazer o mesmo para mudar um valor dentro da hash:
```ruby
calçados["academia"] = "nike"
calçados #=> {"academia"=>"nike","escola"=>"sapato","casa"=> "chinelos", "praia" => "havaianas"}
```
### Removendo elementos
Para remover um elemento de uma hash, basta usar o método `#delete`, que vem com uma funcionalidade de retornar o valor do elemento removido.
```ruby
calçados.delete("escola") #=> "sapato"
calçados #=> {"academia"=>"nike", "casa"=> "chinelos", "praia" => "havaianas"}
```
### Métodos
Hashes e arrays, incrivelmente, tem diversos métodos em comum, já que ambos empregam o módulo **Enumerable** do Ruby.

Alguns métodos que são exclusivos de hashes são o `#keys` e `#values`, que, por incrível que pareça, retornam as **chaves** e os **valores** de um hash. Note que ambos os métodos retornam _arrays_.
```ruby
albuns = {
"BRAZILLIAN SKIES" => "Takanaka",
"MINT JAMS" => "CASIOPEA"
}

albuns.keys   #=> ["BRAZILLIAN SKIES", "MINT JAMS"]
albuns.values #=> ["Takanaka", "CASIOPEA"]
```
### Fundindo dois hashes
Ocasionalmente, você vai precisar fundir dois hashes em uma união matrimonial. Felizmente, temos um método para isso: o `#merge`
```ruby

hash1 = { "a" => 100, "b" => 200 }
hash2 = { "b" => 254, "c" => 300 }
hash1.merge(hash2) #=> { "a" => 100, "b" => 254, "c" => 300 }
```

Perceba que durante a fusão, o `hash2` sobrescreveu os valores similares com o `hash1`.  
Você pode encontrar uma lista completa com todos os métodos de hash nesse link: [Hash class documentation](https://docs.ruby-lang.org/en/3.4/Hash.html).
### Symbols como elementos hash
Nos exemplos iniciais, vimos strings como chaves de hashes. Na prática, porém, você encontrará principalmente symbols (como `:esse_cara`) nessa função. Symbols são mais eficientes que strings em Ruby e resultam em uma sintaxe mais limpa.  
Olha essa belezinha:
```ruby
#sintaxe usando rocket =>
carros_americanos = {
  :chevrolet => "Corvette",
  :ford => "Mustang",
  :dodge => "Ram"
}
#sintaxe usando symbols
carros_japoneses = {
  honda: "Accord",
  toyota: "Corolla",
  nissan: "Altima"
}
```
Cuidado, pois esses métodos tem um jeito diferente de serem chamados do que usando strings. Você precisa utilizar essa sintaxe: `carros_americanos[:chevrolet]`

Ir para o [[Ruby Módulo 8. Métodos]]