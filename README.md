# APLICAÇÃO PARCIAL DE FUNÇÃO

## O que é?
A aplicação parcial de função é um conceito da programação que permite chamar uma função com menos argumentos do que ela espera. Em vez de dar erro, ela retorna uma nova função que "memoriza" os argumentos que já foram fornecidos e fica esperando os argumentos que faltam.

~~~haskell
soma :: Int -> Int -> Int
soma x y =  x + y

soma x = (\y -> x + y)
soma = (\x -> (\y -> x + y))
~~~

## Como é usado?
Em linguagens como Haskell, a aplicação parcial é o comportamento padrão. Uma função que parece aceitar vários argumentos na verdade é uma cadeia de funções que se chamam sequencialmente. Por exemplo, uma função soma x y em Haskell, na verdade, é uma função que pega x e retorna uma nova função que pega y para dar o resultado final.

### Aplicação em Haskell 
~~~haskell
soma :: Int -> Int -> Int
soma x y = x + y

somaDois :: Int -> Int
somaDois = soma 5
~~~

### Aplicação em Python
~~~python
from functools import partial

def multiplicar(a, b):
  return a * b

triplica = partial(multiplicar, 3)
~~~

## Para que é usado?

A aplicação parcial de funções é uma técnica poderosa para

* Reutilizar código: Você pode criar novas funções especializadas a partir de funções genéricas. Por exemplo, a partir de uma função multiplicar, você pode criar funções como dobrar (multiplicar por 2) ou triplicar (multiplicar por 3) sem ter que reescrever a lógica.

* A aplicação parcial é a base da composição de funções, um conceito fundamental da programação funcional. Ela permite que você encadeie várias
funções, onde a saída de uma se torna a entrada da próxima. Isso cria um "pipeline" de dados, tornando o fluxo de informações mais claro.

## Exemplos de codigo 
