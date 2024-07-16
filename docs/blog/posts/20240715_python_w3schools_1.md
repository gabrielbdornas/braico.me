---
date: 2024-07-15
draft: False
authors: [gabrielbdornas]
comments: true
categories:
  - Python
  - Python course
---

# Python 18 Horas - W3schools #1

Junte-se a nós em uma jornada imersiva pelo universo da programação Python! Nos Encontros Python 18Horas, guiados pelos materiais abrangentes do [W3Schools](https://www.w3schools.com/python/default.asp), desvendaremos os segredos dessa linguagem poderosa e versátil, desbravando seus fundamentos e funcionalidades passo a passo.

<!-- more -->

![type:video](https://www.youtube.com/embed/2GMy8TcuQ6A)

## O que foi abordado

* **Introdução ao Python:**
    * Popularidade e aplicações diversas (web, análise de dados, automação etc.).
    * Facilidade de aprendizado e sintaxe intuitiva.
    * Comunidade grande e ativa para suporte.
* **Instalação e uso básico:**
    * Recomendado utilização de ambiente virtual para isolar projetos

    ```python
    # criação ambiente virtual python
    python -m venv venv

    # ativação ambiente virtual linux/mac
    source venv/bin/activate

    # ativação ambiente virtual windows
    source venv/Scripts/activate
    ```

    * Execução de scripts através do interpretador e arquivos `.py`.

* **Sintaxe e indentação:**
    * A importância da indentação para organização e legibilidade do código.

    ```python
    if 5 > 2:
      print('Cinco é maior que 2!')
    ```

    * Erros de indentação e como identificá-los no editor e no interpretador.
    * Boas práticas para formatação de código com tabs (4 espaços).

* **Variáveis:**
    * Conceito e criação através da atribuição de valor.

    ```python
    nome = "Fulano de Tal" # str
    idade = 30 # int
    valor = 4.56 # float
    cidade = "Belo Horizonte" # str
    acertei = True # bool
    ```

    * Armazenamento de dados para uso posterior no código.
    * Diferenças entre variáveis e valores literais.
    * Ausência de declaração formal de tipo de variável no Python.

* **Comentários:**
    * Utilização de hashtags (#) para comentários e documentação do código.

    ```python
    # isto é um comentário
    if 5 > 2: # isto também é um comentário
      print('Cinco é maior que 2!')

    def soma(a, b):
      """
      Este é um comentário para dizer que
      esta função soma dois números, a e b
      """
      return a + b

    print(soma(2, 2))

    # comentário em várias linhas
    # print(soma(2, 3))
    # print(soma(2, 4))
    # print(soma(2, 5))
    ```

    * Desativação de partes do código para testes e depuração.
    * Atalhos para comentar e descomentar linhas e blocos no editor de texto.

## Dicas extras

* Configure o editor de texto para comentar linhas e blocos de código facilmente.
* Configure o editor de texto para salvar automaticamente o arquivo trabalhado (alto-save).
* Utilize o ambiente virtual para cada projeto para isolar bibliotecas e evitar conflitos.
* Este resumo foi elaborado com base na transcrição do encontro e pode conter adaptações para melhor clareza e concisão. Recomendo assistir à gravação para obter uma compreensão mais aprofundada dos tópicos abordados.

## Exercícios

??? question "Defina variáveis para um novo programa de gestão hospitalar"

    - Um novo paciente chamado João deu entrada no hospital. Ele tem 20 anos e é um novo paciente deste hospital. Defina variáveis para armazenar o nome deste paciente, sua idade e se ele é um novo paciente da instituição. Mostre no sistema todas estas informações coletadas.

    ??? "Antes de olhar a resposta, tende fazer sozinho."

        ```python
        nome = 'João'
        idade = 20
        novo_paciente = True
        print(nome, idade, novo_paciente) # (1)!
        ```

        1. :man_raising_hand: Você pode passar mais de um valor para a função `print()`.

## Referências

- [W3schools Python HOME](https://www.w3schools.com/python/default.asp).
- [W3schools Python Intro](https://www.w3schools.com/python/python_intro.asp).
- [W3schools Python Get Started](https://www.w3schools.com/python/python_getstarted.asp).
- [W3schools Python Syntax](https://www.w3schools.com/python/python_syntax.asp).
- [W3schools Python Comments](https://www.w3schools.com/python/python_comments.asp).
- [Python documentation - Whetting Your Appetite](https://docs.python.org/3/tutorial/appetite.html).
- [Python documentation - Using the Python Interpreter](https://docs.python.org/3/tutorial/interpreter.html).
- [Python documentation - An Informal Introduction to Python](https://docs.python.org/3/tutorial/introduction.html).
