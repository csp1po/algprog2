## **Introdução**

Até agora nossos dados desapareciam ao sair do programa.

Arquivos servem para armazenamento permanente

Um arquivo é uma área em disco onde podemos ler ou gravar informações.

Acessamos o arquivo pelo seu nome.

> *Para acessar um arquivo é preciso abri-lo*

Vimos também exemplos de programas que obtiveram os dados de entrada de usuários via teclado.

```nomes = input()```



*   A maioria desses programas pode receber seus dados de entrada de arquivos texto também.
*   Um arquivo texto armazena caracteres que podem ser mostrados diretamente na tela ou modificados por um editor de textos simples. Exemplos: código python, documento texto simples, páginas HTML.




Ao **abrir** o arquivo informamos seu `nome`, `diretório` onde fica (se necessário) e que operações iremos executar: **leitura** e/ou **escrita**

A função que abre os arquivo é `open` e os modos de abertura são:
*   r: leitura
*   w: escrita
*   a: append
*   b: binário
*   +: atualização

Os métodos para ler ou escrever são `read` e `write`

> **Observação: os arquivos devem ser fechados com `close`**

## **Arquivos Textos**

*   Quando comparado à entrada de dados via teclado, as principais vantagens de se obter dados de entrada de um arquivo são:
*   O conjunto de dados pode ser muito maior.
*   Os dados podem ser inseridos muito mais rapidamente e com menos
chance de erro.
*   Os dados podem ser usados repetidamente com mesmo programa ou com diferentes programas.



## **Arquivos Textos**

*   Um nome e caminho únicos são usados por usuários ou em programas ou scripts para acessar um arquivo texto para fins de leitura e modificação.
*   As tarefas básicas envolvidas na manipulação de arquivos são **ler** dados de arquivos e **escrever** ou anexar dados em arquivos.
*   Leitura e escrita em arquivos em Python são muito fáceis de gerenciar.


## Observe o exemplo abaixo

**Observações:**

*   Para se trabalhar com arquivos devemos abri-lo e associá-lo com uma variável.
*   A variável será um objeto do tipo file que contém métodos para ler e escrever no arquivo.
*   O primeiro passo então é abrir o arquivo com o comando open:

Exemplo:
```python
variavel_arquivo = open("nome do arquivo", "modo")
```
*   O "*nome do arquiv*o" pode ser relativo ou absoluto.
*   O "modo" pode ser "r"(leitura), "r+"(leitura e escrita), "w"(escrita), "a"(append).



```python
arquivo = open('numeros.txt', 'w')
for linha in range(1, 101):
  arquivo.write(f"{linha}\n")

arquivo.close()

```

Caso você execute este programa nada aparecerá na tela.

Procure no diretório do programa o arquivo `números.txt`

O modo `w` cria o arquivo se ele não existir, caso exista ele será apagado e reescrito


```python
arquivo = open('numeros.txt', 'r')
for linha in arquivo.readlines():
  print(linha)

arquivo.close()
```

`readlines()` gera uma lista onde cada elemento é uma linha lida

Arquivos textos são simples e possuem um caracter de controle no final para pular linha

Se quisermos tirar esse caracter do final podemos usar

```print(linha.rstrip())```

## E como trabalhar com arquivos de uma forma _pythonica_ (_pythonic way_)?

Observe o código abaixo.


```python
with open('numeros.txt') as f:
  print(f.read())
```

*   O código acima faz o mesmo mas de uma maneira "pythônica"
*   Vimos acima como programadores normais fazem a leitura (maneira não pythonica)
*   Python é legal, pois sempre você pode se aprofundar mais
*   Python é simples, mas difícil de esgotar

## **Exemplo #1**

Leia o arquivo `mensagem.txt` e grave em num novo arquivo chamado `cripto.txt` com todas as vogais trocadas por ‘*’


```python
texto = open('mensagem.txt')
saida = open('cripto.txt', 'w')
for linha in texto.readlines():
  for letra in linha:
    if letra in 'aeiou':
      saida.write('*')
    else:
      saida.write(letra)

texto.close()
saida.close()
```

## **Exemplo #2**

*   Páginas web são escritas em `HTML` (Hypertext Mark-up Language)
*   Tags HTML começam com `<` e terminam com `>`
*   A página web é escrita entre `<html>` e `</html>` que é a tag de maior nível
*   Normalmente inserimos código javascript
*   Javascript não é um subconjunto de Java


```python
arquivo = open('ola.html', 'w', encoding='utf-8')
arquivo.write('''<!DOCTYPE html>
<html lang="pt-BR")
<head>
<meta charset="utf-8">
<title>Título da Página</title>
</head>
<body>
<h1>Olá</h1>
</html>''')
arquivo.close()
```

> **Observe o parâmetro de codificação `utf-8`. Sem ele os acentos não sairão**

## **Resumo comando `open`**

Modo  | Operador | Indicador de Posição
----- | -------- | -----------
r     | leitura  |  início do arquivo
r+    | leitura e escrita | início do arquivo
w     | escrita  | início do arquivo
a     | (append) escrita | final do arquivo

## **Observações Importantes**

*   Se um arquivo for aberto para leitura (`r`) e ele não existir, open gera um erro.
*   Se um arquivo for para escrita (`w`) e existir, ele é sobrescrito. Se o arquivo não existir, um novo arquivo é criado.
*   Se um arquivo for aberto para leitura/escrita (`r+`) e existir, ele não é apagado.
*   Se o arquivo não existir, `open` gera um erro.





