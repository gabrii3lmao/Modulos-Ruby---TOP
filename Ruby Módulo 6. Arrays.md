 Ruby, uma das formas de representar uma coleção de dados é com um `array`, que pode ser resumido a uma lista ordenada.

### Criando arrays
Aqui está 2 arrays básicos: 
``` ruby
num_arr = [24, 69, 17, 22, 13]
str_arr = ["este", "array", "é", "muito", "pequeno"] #foi o que ela disse
```
Arrays são geralmente criados como `arrays literais`, que é uma sintaxe especial usada para criar instancias de objetos. Para criar um array usando um array literal, use colchetes ([]).

Um array também pode ser usado criando um método `Array.new`. Quando Você chama esse método, você pode usar 2 argumentos opcionais(tamanho inicial e valor padrão)
``` ruby
Array.new               #=> []
Array.new(3)            #=> [nil, nil, nil]
Array.new(2, "Bom dia familia") #=> ["Bom dia familia", "Bom dia familia"]
Array.new(3, true)      #=> [true, true, true]
```

### Acessando elementos
O Ruby contabiliza as posições a partir do 0, o que significa que a primeira posição sempre vai ser 0. Para acessar o index de um array, basta usar essa sintaxe: `my_arr[x]`

``` ruby
#Onde você está na fila do pão?
str_array = ["fila", "da", "padaria", "bem", "pequena"]

str_array[0]            #=> "fila"
str_array[1]            #=> "da"
str_array[4]            #=> "padaria"
str_array[-1]           #=> "pequena"
str_array[-2]           #=> "bem"
```

O Ruby também disponibiliza alguns métodos como `#first` e `#last`, que são bem explícitos. Esses métodos também recebem um argumento opcional, que retornará um novo array que contém a primeira ou o último elemento `n` de `my_array`, respectivamente.
``` ruby
fila_do_pao = ["eu", "aposentada1", "aposentada2", "aposentada3", "dono de imóvel"]

fila_do_pao.first     #=> "eu"
fila_do_pao.first(2)  #=> ["eu", "aposentada1"]
fila_do_pao.last(2)   #=> ["dono de imóvel", "aposentada3"]
```

### Adicionando e removendo arrays
Para adicionar um elemento a um array, você pode usar o método `#push` ou o operador `<<` (shovel). Ambos os métodos irão adicionar um elemento ao final do array. 
O método `#pop` irá remover o último elemento do array e irá retornar o elemento removido.
``` ruby
num_array = [1, 2]

num_array.push(3, 4)    #=> [1, 2, 3, 4]
num_array << 5          #=> [1, 2, 3, 4, 5]
num_array.pop           #=> 5
num_array               #=> [1, 2, 3, 4]
```
Os métodos `#unshift`e `#shift` são usados para adicionar e remover os elementos no começo do array,  respectivamente.  Assim como `#pop` remove do final, `#shift` remove do início, 
ambos retornando o elemento removido.
``` ruby
caminhao_cimento = ["saco1", "saco2", "saco3"]

caminhao_cimento.shift          #=> "saco1"
caminhao_cimento.unshift("saco1")  #=> ["saco1", "saco2", "saco3"]
```
### Adicionando e subtraindo arrays
Somando 2 arrays vai retornar um somo array construído a partir da concatenação entre eles, igual acontece com strings.
``` ruby
a = [1, 2, 3]
b = [3, 4, 5]

a + b        #=> [1, 2, 3, 3, 4, 5]
a.concat(b)  #=> [1, 2, 3, 3, 4, 5]
```
Para encontrar a diferença entre 2 arrays, você pode subtraí-los usando o sinal de `-`. Esse método retorna uma cópia do primeiro array sem os elementos do segundo
``` ruby
[1, 1, 2, 2, 3, 4, 4, 4, 1] - [1, 4]  #=> [2, 2, 3]
```

### Alguns métodos 
Aqui estão alguns métodos muito uteis que o próprio Ruby disponibiliza: 

``` ruby
[].empty?               #=> true
[[]].empty?             #=> false
[1, 2].empty?           #=> false

[1, 2, 3].length        #=> 3

[1, 2, 3].reverse       #=> [3, 2, 1]

[1, 2, 3].include?(3)   #=> true
[1, 2, 3].include?("3") #=> false

[1, 2, 3].join          #=> "123"
[1, 2, 3].join("-")     #=> "1-2-3"

# o Método #map não modifica o array original
[1, 2, 3, 4].map{ |num| num**2} #=> [1, 4, 9, 16]

# o método #delete_at modifica o array original
[1, 2, 3, 4].delete_at(1)       #=> 2 [1, 3, 4]

[1, 1, 3, 3, 5, 5, 5, 6].uniq   #=> [1, 3, 5, 6]

[1, 2, 3].sample      #=> elemento aleatório
[1, 2, 3].shuffle     #=> array embaralhado
[1, 2, 3].index(2)    #=> 1 (encontra índice)
[1, 2, 3, 4].select { |n| n.even? } #=> [2, 4] (filtro)
```

Ir para o [[Ruby Módulo 7. Hashes]]