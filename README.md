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

### Exemplo 1 
~~~haskell
subtrair :: Int -> Int -> Int
subtrair x y = x - y

subtrairDinheiroDaConta :: Int -> Int
subtrairDinheiroDaConta = subtrair 1000
~~~



![Exemplo 1](https://cdn.discordapp.com/attachments/1322192439141990402/1410421278363615252/2025-08-27-21-13-46.gif?ex=68b0f4ad&is=68afa32d&hm=e7d9f4d2dc12adfe537d6caa139cd9ecb57fcf2687fb9c2259d693ad0e0a257a&)

### Exemplo 2
~~~haskell
numeros :: [Int]
numeros = [1,3,7,8,9]

adicionar :: Int -> Int -> Int
adicionar x y = x + y

adicionarDez :: Int -> Int
adicionarDez = adicionar 10

numerosAumentados = map adicionarDez numeros
~~~



![Exemplo 2](https://cdn.discordapp.com/attachments/1322192439141990402/1410420271608889424/2025-08-27-21-17-20.gif?ex=68b0f3bd&is=68afa23d&hm=9ebe262d300a614a44c215020b021dd0216136462666c07256158a63b22357fd&)


### Exemplo 3
~~~haskell
criarEmail :: String -> String -> String -> String
criarEmail remetente assunto mensagem =
  "De: " ++ remetente ++ "\n" ++
  "Assunto: " ++ assunto ++ "\n" ++
  "Mensagem: " ++ mensagem ++ "\n"

emailDeSuporte :: String -> String -> String
emailDeSuporte = criarEmail "suporte@empresa.com"

emailDeProblemaDeLogin :: String -> String
emailDeProblemaDeLogin = emailDeSuporte "Problema com o Login"

email1 = emailDeSuporte "Novo Cadastro" "Bem-vindo à nossa plataforma!"
email2 = emailDeProblemaDeLogin "Não consigo acessar minha conta. Por favor, ajudem!"
~~~



![Exemplo 3](https://cdn.discordapp.com/attachments/1322192439141990402/1410419812542316644/2025-08-27-21-18-35.gif?ex=68b0f34f&is=68afa1cf&hm=11aa02e982a9d23503770d78cba28b4d2d442ec027bb8c53f762f59586db2ef0&)

## Referências

<https://haskell.tailorfontela.com.br/higher-order-functions>
<https://en.wikipedia.org/wiki/Currying>
<https://youtu.be/m12c99qgHBU>

