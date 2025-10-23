
Relembrando o que é um método predicado, são aqueles métodos que terminal com `?` ao final do nome, como `#método?` e retornam true ou false. Porém, nesse módulo, veremos os métodos enumeráveis de predicado.
### O método `#include?`
Se quisermos saber se um certo elemento existe dentro de um array, podemos usar o método `#include?`. Esse método retorna `true` se o elemento existir dentro de um array ou hash, e `false` se não existir.
``` ruby
nomes = ["gabriel", "junior", "lucas", "ellen", "anita"]
nomes.include?("alex")
#=> false
```
### O método `#any?`
Este método retorna `true` se algum elemento dentro do array condiz com a condição que foi imposta. Se não, ele retornará `false`.

Vamos ver se existe algum número maior que 50 e menor que 500 neste array:
``` ruby
numeros = [50, 5000, 500, 200, 750, 200]
numeros.any?{|number| number > 50 && number < 500}
#=> true
``` 

Não confunda. Ele não irá retornar os elementos que batem com a condição. Apenas irá dizer se tem ou se não tem.
### O método `#all?`
O método `#all?` irá retornar true se TODOS. TODOS OS ELEMENTOS condizerem com a condição que você impôs no bloco.
``` ruby
moedas = [0.10, 0.25, 0.50, 1]
moedas.all?{|moeda| moeda > 0.05}
#=> true
```
### O método `#none?`
O método `#none?` funciona exatamente o oposto do método `#all?`. Ele retornará `true` apenas se todos os elementos do array *NÃO* condizerem com a condição imposta no bloco. Por outro lado, retornará `false`.
``` ruby
meus_arrays = [[1, 2, 3], [4, 5, 6, 7], [8, 9], [10]]
meus_arrays.none?{|array| array.length > 5}
#=> true
```
### O método `#one?`
E se quiséssemos que apenas um elemento do array batesse com a nossa condição? Apenas um. Sem mais, nem menos. Um. o método `#one?` está aí para te ajudar: 
``` ruby
comidas_calorias = {
"hambúrguer": 500,
"pizza": 600,
"chocolate": 200,
"mamão": 20
}

comidas_calorias.one?{|comida| comida < 100}
#=> true
```

Ir para o [[Ruby Cap1 Módulo 11. Nested collection]]
