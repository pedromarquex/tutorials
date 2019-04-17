# Configurando ambiente de desenvolvimento Python

No mundo da programação, sabemos que existem certas regras que devemos seguir quando se trata de qualidade de software. Tais regras podem ser extendidas também para a organização do projeto, o que facilita ainda mais sua manutenção.

Neste tutorial, vamos configurar de maneira simples e eficar nosso ambiente Python de forma isolada, utilizando as melhores ferramentas pra isso. Utilizar ambientes de desenvolvimentos isolados pode nos livrar de conflitos de dependências e a possibilidade de manter projetos paralelos que utilizam versões diferentes dos mesmos pacotes e bibliotecas.

O que você vai aprender:

* Instalar o Python 3
* Instalar o virtualenv e isolar seu ambinte de desenvolvimento
* Usar o pip para guardar as dependências do seu projeto

# Instalando o Python 3

Primeiramente, vamos acessar o [site oficial do Python](https://www.python.org/downloads/) e proceder com o download da versão mais estável do Python. O site também dispõe de tutoriais de instalação do pacote para os mais diversos sistemas operacionais.

**IMPORTANTE: no Windows, ao fazer a instalação, não se esqueça de marcar a opção "adicionar Python ao PATH"**

Feito isso, podemos executar o seguinte comando para verificar se a instalação ocorreu corretamente, o que deve retornar a versão do Python que você acabou de instalar:

```
$ python --version
```

Caso o comando não tenha o retorno esperado, talvez a instalação não tenha ocorrido com sucesso.

## Extra: Atualizando o pip

Como toda linguagem moderna, o Python também conta com um gerenciador de pacotes. O que vamos utilizar neste tutorial será o [pip](https://pypi.org/project/pip/). Com ele nós poderemos realizar a instalação de pacotes python diretamente dos repositórios oficiais. No site oficial supra citado você encontra também a documentação, bem como a lista de pacotes disponíveis para download.

Para que o funcionamento do pip ocorra como esperamos, é importante mantê-lo sempre atualizado. Quando instalamos o Python, por padrão, já temos uma versão do pip instalada e podemos verificar esta versão com o comando:

```
$ pip --version
```

Podemos fazer a atualização pip utilizando ele próprio, mas o faremos com o comando que utiliza o Python para evitar alguns problemas que por ventura possam ocorrer. Para atualizar o pacote, devemos apenas executar o comando:

```
$ python -m pip install -U pip
```

Agora, se verificarmos novamente a versão do pip veremos que o pacote foi devidamente atualizado.

# Instalando e utilizando o virtualenv

Depois de ter instalado o Python com sucesso e atualizado o pip, podemos prosseguir para o próximo passo que é instalar uma das muitas ferramentas que nos permite isolar nosso ambiente de desenvolvimento python. Neste tutorial, utilizaremos o virtualenv.

Sua instalação é simples e pode ser feita utilizando o gerenciador de pacotes pip, com o comando:

```
$ pip install virtualenv
```

Agora vamos de fato criar nosso ambiente de desenvolvimento e isolá-lo do nosso sistema operacional. Antes disso tenha certeza de que está na pasta que você criou do seu projeto e então rode o comando:

```
$ virtualenv venv
```

Se você tem apenas uma versão do Python instalada no seu computador, não terá nenhum problema. O processo deve ser rápido e após isso você já terá seu ambiente Python criado e, o mais importante, **isolado** do restante do seu sistema operacional. 

Agora podemos notar que temos na raiz do nosso projeto uma pasta chamada *venv* que é exatamente o nome que costumamos dar quando criamos nosso ambiente, e dentro delas podemos ver as pastas *bin, include e lib*, no caso de sistemas baseados em Unix, e no Windows no lugar de *lib* teremos *Scripts*, que é onde ficam nossos scripts do ambiente.

Finalmente vamos ativar nosso ambiente de desenvolvimento. Estando na raiz do nosso projeto, executamos o seguinte comando: 

em sistemas baseados em Unix (Linux, MacOS):
```
$ source venv/bin/activate
```

no Windows:
```
$ venv\Scripts\activate
```
Com isso teremos agora no terminal uma indicação de que o nosso ambiente virtual está ativado:

```
$ (venv) [user@computer raiz_projeto]$
```

E de agora em diante, todos os pacotes que instalar-mos usando o pip ficarão somente neste espaço isolado do sistema operacional. Você pode criar quantos ambientes virtuais desejar para seus projetos, não tenha medo de experimentar.

Ao termino da atividade de desenvolvimento, podemos também desativar nosso ambiente virtual com um simples comando: 

```
$ deactivate
```

# Guardando as dependencias do projeto com o pip

Em cada projeto que costumamos desenvolver, geralmente instalamos vários pacotes separados, cada um com sua versão específica. Posteriormente, quando quisermos mudar de máquina ou até mesmo ter uma relação de cada pacote utilizado no projeto, cada um com sua versão, podemos deixar que o pip nos ajude com isso automáticamente.

Tendo certeza que estamos na raiz do nosso projeto e com nosso ambiente virtual ativado, utilizaremos o seguinte comando:

```
$ pip freeze > requeriments
```

Com este comando, será criado um arquivo chamado *requeriments* que conterá todas os pacotes instalados no nosso ambiente, com suas respectivas versões.

Posteriormente podemos utilizar este mesmo arquivo para instalar essas dependências em outra venv com o comando:

```
$ pip install -r requeriments
```
