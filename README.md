#**Dicionários - O que é?**

Idêntico as listas, um dicionário é uma coleção mutável de vários valores.

Todavia, difentemente das listas, os dicionários podem usar dados de tipos diferentes. Ou seja, não somente valores inteiros. Estes índices, quando se trata de dicionários, são chamados de *chaves* (*keys*), e uma chave, juntamente com o seu valor associado é chamado de *par chave-valor* (*key-value pair*).

Quando usado no código, um dicionário é digitado com chaves, isto é, ``{}``.

```python
myCat = {'size': 'fat', 'color': 'gray', 'disposition': 'loud'}
```

Observando o trecho de código acima, atribuiu-se um dicionário à variável ``myCat``. As chaves (_keys_) são ``'size'``, ``'color'``, e ``'dispositon'``.

Os valores dessas chaves são ``'fat'``, ``'gray'``, e ``'loud'``, respectivamente.


##**Como acessar estes valores?**

```python
myCat['size']
'fat'
```

```python
print("My cat has " + myCat['color'] + ' fur' )
```

> **Observação**: dicionários também podem utilizar valores inteiros como chaves, assim como as listas fazem. Porém, elas não precisam começar em 0. E mais, qualquer número pode ser usado. Veja o exemplo abaixo.

```python
spam = {12345: 'Luggage Combination', 42: 'The Answer'}
```


## **Como adicionar valores a um dicionário?**


```python
# cria um dicionário vazio
d = {}

#atribui o par (chave-valor)
d['a'] = 'alpha'
d['o'] = 'omega'
d['g'] = 'gama'

#d = {'a': 'alpha', 'o': 'omega', 'g': 'gama'}

#imprime o dicionário (dict)
print(d)
```

    {'a': 'alpha', 'o': 'omega', 'g': 'gama'}



```python
# imprime o valor correspondente à chave 'a'
d['a']
```




    'alpha'




```python
# imprime o valor correspondente à chave 'x'
d['x']
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-10-34b0b3efbbd9> in <cell line: 2>()
          1 # imprime o valor correspondente à chave 'x'
    ----> 2 d['x']
    

    KeyError: 'x'


##**Dicionários versus Listas**

Diferentemente das listas, os itens de um dicionário não estão ordenados. Ou seja, o primeiro item de uma lista ``spam`` será sempre ``spam[0]``. Entretanto, não existe um "primeiro" item em um dicionário.

Enquanto a ordem dos itens é importante para determinar se duas listas são iguais, não importa em que ordem os pares _chaves-valor_ são digitados em um dicionário. Digite os trechos de código abaixo e execute-os.



```python
spam = ['cats', 'dogs', 'mooses']
bacon = ['dogs', 'mooses', 'cats']
spam == bacon
```

---

```python
eggs = {'name': 'Sophie', 'species': 'cat', 'age': '8'}
ham = {'species': 'cat', 'age': '8', 'name': 'Sophie'}
eggs == ham
```


> **Observação #1**: Pelo fato de não serem ordenados, dicionários não podem ser fatiados (_sliced_).

> **Observação #2**: Caso você tente acessar uma chave inexistente, isto resultará em uma mensagem de erro ``KeyError``, que é semelhante à mensagem ``IndexError`` que se refere a "fora do intervalo" (_out-of-range_) em uma lista. Veja o código abaixo.

---

```python
spam = {'name': 'Sophie', 'age': 7}
spam['color']
```

---

Apesar de que os dicionários não estejam ordenados, o fato de poder haver valores arbitrários para chaves permite que você organize seus dados de maneiras eficientes.

> Exemplo: suponha que você queira armazenar dados relativos às datas de aniversário de seus amigos. Pode-se usar um dicionário com os nomes como chaves, e as datas de aniversário como valores. Vejamos o código abaixo.


```python
birthdays = {'Alice': 'Apr 1', 'Bob': 'Dec 12', 'Carol': 'Mar 4'}

while True:
  print('Enter a name: (blank to quit)')
  name = input()
  if name == '':
    break

  if name in birthdays:
    print(birthdays[name] + ' is the birthday of ' + name)
  else:
    print('I do not have birthday information for ' + name)
    print('What is their birthday?')
    bday = input()
    birthdays[name] = bday
    print('Birthday database updated.')

print(birthdays)
```

> #### **Observação: é claro que todos os dados fornecidos pelo programa acima serão esquecidos quando o programa terminar.**

> #### **Futuramente vamos aprender como salvar dados em arquivos no disco rígido do seu computador.**

## **Métodos ``keys()``, ``values()`` e ``items()``**


Existem três métodos de dicionário que retornam valores semelhantes a listas, contendo as chaves (_keys_), os valores (_values_)ou ambos (_items_). Vejamos alguns exemplos.


```python
spam = {'color': 'red', 'age': 42}

# um loop for faz a iteração e percorre cada um
# dos valores no dicionário ``spam``
for v in spam.values():
  print(v)
```
---

```python
# um loop for faz a iteração e percorre cada uma
# das chaves no dicionário ``spam``
for k in spam.keys():
  print(k)
```

---

```python
# um loop for faz a iteração e percorre cada um
# dos pares chaves-valor no dicinário ``spam``
for i in spam.items():
  print(i)
```

---


> Observe que os valores retornados pelo método ``items()`` são tuplas contendo a chave e valor.

> Caso queira uma lista de verdade a partir de um desses métodos, passe o valor de retorno semelhante à uma lista, usando a função ``list()``


```python
spam = {'color': 'red', 'age': 42}
spam.keys()

# converte uma tupla em uma lista
list(spam.keys())
```

---

> **Você também pode usar o truque de atribuição múltipla em um loop `for` para atribuir a chave e o valor a variáveis separadas. Observe o código abaixo.**


```python
spam = {'color': 'red', 'age': 42}
for k, v in spam.items():
  print('Key: ' + k + ' Value: ' + str(v))
```

---


## **Verificando se uma chave ou valor existe em um dicionário**


```python
spam = {'name': 'Sophie', 'age': 7}

'name' in spam.keys()
```


```python
'Zophie' in spam.values()
```



```python
'color' in spam.keys()
```



```python
'color' not in spam.keys()
```


```python
'color' in spam
```


### **O método `get()`**

É "chatinho" verificar se uma chave existe em um dicionário antes de acessar o valor dela. Felizmente, os dicionários têm um método chamado `get()` que aceita dois argumentos: a chave do valor a ser recuperado e um valor alternativo a ser retornado se essa chave não existir.

Observe o trecho de código abaixo.


```python
picnicItems = {'apples': 5, 'cups': 2}
print('I am bringing ' + str(picnicItems.get('cups', 0)) + ' cups.')
```


```python
print('I am bringing ' + str(picnicItems.get('eggs', 0)) + ' eggs.')
```


> **Como não há chave `eggs` no dicionário `picnicItems`, o valor padrão 0 é retornado pelo método `get()`. Sem usar este método, o código causaria uma mensagem de erro, como no exemplo abaixo**


```python
picnicItems = {'apples': 5, 'cups': 2}
print('I am bringing ' + str(picnicItems['eggs']) + ' eggs.')
```

---


### **O método `setdefault()`**

Muitas vezes, você terá que definir um valor em um dicionário para uma determinada chave somente se essa chave ainda não tiver um valor. Observe o trecho de código usando a forma tradicional (sem o método).


```python
spam = {'name': 'Pooka', 'age': 5}
if 'color' not in spam:
  spam['color'] = 'black'
```

O método `setdefault()` oferece uma maneira de fazer isso em apenas uma linha de código. O primeiro argumento passado para o método é a chave a ser verificada e o segundo argumento é o valor a ser definido nessa chave **se ela não existir**. Caso exista, o método `setdefault()` retorna o valor da chave.
Observe os trechos de código abaixo.


```python
spam = {'name': 'Pooka', 'age': 5}
print(spam.setdefault('color', 'black'))
spam
```

> Na primeira vez que é chamado, o dicionário `spam` muda para `{'name': 'Pooka', 'age': 5, 'color': 'black'}`.

> O método retorna o valor `'black'` porque agora é o valor definido para a chave `'color'`.


```python
print(spam.setdefault('color', 'white'))
spam
```



> Quando spam.setdefault('color', 'white') é chamado em seguida, o valor dessa chave não é alterado para 'white', porque o spam já tem uma chave chamada 'color'.


##### **O método `setdefault()` é um bom atalho para garantir que uma chave exista**

# **Exemplos Práticos**


```python
# Exemplo 1: Acessar Valor por Chave
# Acesse o valor associado a uma chave específica em um dicionário.

person = {'name': 'John', 'age': 25, 'city': 'New York'}
print(person['age'])

```


```python
# Exemplo 2: Adicionar Elementos
# Adicione um novo par chave-valor a um dicionário existente.

student = {'name': 'Alice', 'age': 20}
student['grade'] = 'A'
print(student)

```


```python
# Exemplo 3: Verificar Existência de Chave
# Verifique se uma chave específica existe em um dicionário.

inventory = {'apples': 10, 'bananas': 5, 'oranges': 8}
if 'apples' in inventory:
    print("We have apples!")

```


```python
# Exemplo 4: Atualizar Valores
# Atualize o valor associado a uma chave existente em um dicionário.

book = {'title': 'Python Programming', 'pages': 300}
book['pages'] = 350
print(book)

```


```python
# Exemplo 5: Remover Elemento
# Remova um par chave-valor de um dicionário.

settings = {'theme': 'dark', 'font_size': 12, 'language': 'English'}
removed_value = settings.pop('font_size')
print(settings)

```


```python
# Exemplo 6: Chaves e Valores
# Obtenha uma lista das chaves e dos valores de um dicionário.

scores = {'Math': 90, 'Science': 85, 'History': 75}
keys = list(scores.keys())
values = list(scores.values())
print("Keys:", keys)
print("Values:", values)
```


```python
# Exemplo 7: Iterar sobre Chaves e Valores
# Itere sobre as chaves e os valores de um dicionário usando um loop.

menu = {'burger': 5, 'fries': 3, 'drink': 2}
for item, price in menu.items():
    print(f"{item}: ${price}")

```


```python
# Exemplo 8: Tamanho do Dicionário
# Calcule o número de pares chave-valor em um dicionário.

animals = {'dogs': 4, 'cats': 2, 'birds': 1}
num_animals = len(animals)
print("Number of animals:", num_animals)

```


```python
# Exemplo 9: Dicionário de Notas
# Crie um dicionário para armazenar notas de alunos e calcule a média.

grades = {'Alice': 85, 'Bob': 70, 'Carol': 92}
total_score = sum(grades.values())
average_score = total_score / len(grades)
#print("Average score:", average_score)
print(f"Average score: {average_score:.2f}" )

```


```python
# Exemplo 10: Mesclar Dicionários
# Mesclar dois dicionários em um único dicionário.

dict1 = {'a': 10, 'b': 20}
dict2 = {'b': 15, 'c': 30}
# usando a técnica de "desempacotamento de dicionário"
# ela é usada para desempacotar os itens de um dicionário
# e passá-los como argumentos nomeados para uma função ou
# para criar um novo dicionário combinando os itens de vários dicionários.
merged_dict = {**dict1, **dict2}
print(merged_dict)

# usando o operador de união
# a partir da versão Python 3.9
merged_dict = dict1 | dict2
print(merged_dict)
```

