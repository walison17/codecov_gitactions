# codecov_gitactions
Adicionado Codecov com GitHub Actions

[![codecov](https://codecov.io/gh/agnoliveira/codecov_gitactions/branch/main/graph/badge.svg?token=LCDJ17XTBT)](https://codecov.io/gh/agnoliveira/codecov_gitactions)

# Codecov com GitHub Actions e Pipenv - Passo a passo

1 -  Crie o repositório no GitHub e após acesse o site https://codecov.io

2 - Faça o cadastro e login com o GitHub e depois clique em "Add new repository"
Obs.: Se for o primeiro acesso o GitHub vai pedir autorização de acesso e deverá aparecer quais repositórios serão permitidos. Caso não seja o primeiro acesso, vá em Settings da conta do GitHub e no menu Applications, clique em Configure no Codecov e autorize o repositório que pretende integrar.

3 - Em seu repositório no GitHub, vá na aba Actions e procure por "Python application" e clique em "Set up this workflows".

4 - Na tela seguinte, você deve entrar com a configuração do arquivo Worklows. Delete o conteúdo e cole o conteudo do mesmo arquivo deste repositório. O caminho do arquivo é: codecov-gitactions/.github/workflows/codecov-ga-project.yml
Obs.: Lembre-se de mudar a versão do Python 3.9 do arquivo para sua versão utilizada.\
Se seu repositório for Privado, precisará acrescentar no arquivo o Token, como exemplo abaixo:

```
- name: Posting Coverage
      env:
        CODECOV_TOKEN: "aaaaaaa-a096-4dfd-9c84-xxxxxxxxxxxx"
  run: |
        pipenv run codecov
```
E o token, devera ser trocado pelo seu. Para pegá-lo, acesse o site https://codecov.io, acesso o repositório e vá em settings.\
Após finalizado a edição do arquivo, de um nome para ele e clique em "Start commit".

5 - Adicionando o distintivo do Codecov no README:
* Entre no site https://codecov.io/ e clique em "Settings" do seu repositório.Lá clique no menú Badge e copie o código de Markdown.
* Volte no repositório do GitHub e edite o arquivo Readme e cole esse código, após clique em commit para salvar o arquivo.

6 - No computador local, faça o clone do seu repositório.
* Feito isso, instale as dependências com o comando:

```pipenv install pytest coverage pytest-cov codecov --dev```

7 -  Agora vamos criar um teste simples para testar no codecov:
* Crie na raiz do projeto um "Python Package" com o nome de tests e dentro dele um "Python File" com qualquer nome, neste caso: test_codecov.py e dentro desse arquivo entre com o código abaixo:
```
def test_codecov():
    assert 1 == 1
```    

* Depois crie uma nova branch, faça commit e push e depois volte ao GitHub e clique em "Compare & pull request" e depois em "Create pull request"