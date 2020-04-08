
## Criando venv (ambiente virtual) e um projetinho básico

Este arquivo vai servir para fazer o passo a passo das minhas ações para poder avaliar elas no futuro.

Estou usando **Windows + VSCode**.

Primeiro, use o pip pra instalar o venv:
`pip install virtualenv`

Segundo, crie o local onde ficará seu ambiente virtual. Como eu criei uma pasta chamada *`venv-aula-demonstracao`* e estou dentro dela, só preciso rodar:
`python -m venv .\venv-aula-demonstracao`

Terceiro, ative o ambiente virtual:
`.\venv-aula-demonstracao\scripts\activate.ps1`

Para cada sistema operacional, o comando pra ativar o venv é diferente, então, se você está executando em Mac ou Linux, verifique o site do [venv](https://docs.python.org/3/library/venv.html)

Crio a pasta hello e adiciono dentro dele dois arquivos: `__init__.py` e `hello.py`.

Se eu executar na linha de comando (**cmd**) agora `python hello/hello.py`, terei a resposta `Hello, world`.

Agora, crio arquivo `setup.py` na raiz do projeto com algum conteúdo e executo `python setup.py build` no cmd.

Será gerada uma pasta chamada `build` com os arquivos que eu possuo na minha aplicação.

Também posso gerar um arquivo compactado (zip) usando o comando `python setup.py sdist`.

E se executar `python setup.py install`, o python vai instalar o nosso pacote como um import pronto para ser utilizado.

Se eu executar no cmd `pip freeze`, o python irá mostrar todas as bibliotecas (libs) que estão instaladas na venv que está ativa.

No meu caso, agora, são estas:
- Aula-demonstra-o-de-venv==0.0.1
- numpy==1.18.2
- pandas==1.0.3
- python-dateutil==2.8.1
- pytz==2019.3
- six==1.14.0

Se eu quiser compartilhar meu projeto com alguém, posso rodar `python freeze > requirements.txt` e terei o arquivo `requirements.txt` que posso enviar as pessoas que desejo.

Elas poderão executar `pip install -r requirements.txt`. Isso fará com que o python baixe todos os requisitos para essa pessoa rodar meu projeto.

Criei o arquivo makefile que é um compilar de linguagens que vem com o Linux mas como estou com o Windows, não vou instalá-lo para ver como funciona.

Mas para rodar é basicamente `make python` e a função que tu quer rodar, assim `make python install`

A estrutura é:
Alvo: dependencias para executa o alvo
    comandos

Por exemplo:
install: sdist
	@python setup.py install

Para executar isso, seria `make python install` e isso vai primeiro executar o *`sdist`* porque é uma dependencia para depois rodar *`install`* que tem como comando `@python setup.py install`.

Por fim, adicionei o jupyter usando `pip install jupyter` porque aí você pode rodar `jupyter notebook` que ele se responsabiliza por subir um servidor pra criar seus notebooks.

Basta clicar no link que ele gerar ou digitar no navegador `localhost:8888` e informar o token que ele gerou.

Finalizei adicionando o script para atualizar o pip de vocês `python -m pip install --upgrade pip` para versão 20.0.2.