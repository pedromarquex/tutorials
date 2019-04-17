# Guia rápido JavaScript ES6 - Configurando o ambiente

Este tutorial tem como objetivo de mostrar rapidamente tudo que você precisa iniciar seu projeto JavaScript, configurando o ambiente para produção.

O que você vai aprender:

* Instalar o Node e o Yarn
* Inicializar o projeto com Yarn
* Instalar e configurar o Babel

## Instalando NodeJS e Yarn

Baixe o pacote do Node em [NodeJS download](https://nodejs.org/en/download/) e faça a instalação normalmente, de acordo com seu sistema operacional. Após a instalação, a versão do Node pode ser verificada pelo terminal com o comando:
```
$ node -v
```

As intruções para a instalação do gerenciador de pacotes Yarn podem ser acessadas em [Yarn package installation](https://yarnpkg.com/lang/en/docs/install/#debian-stable). Neste link também há instruções para instalação em diversos sistemas operacionais. Depois da instalação também podemos verificar a versão que foi instalada com um comando no terminal:

```
$ yarn -v
```

## Iniciando o projeto com Yarn

Para inicializar nosso projeto podemos criar uma pasta onde armazenaremos nosso código e inizializar nosso repositório com o Yarn com os comandos:

```
$ mkdir projeto
$ cd projeto
$ yarn init
```

Este ultimo comando vai nos retornar uma séria de perguntas, que você pode optar por responder ou deixar em branco apenas apertando *< enter >* em todas.


## Instalando e configurando o Babel

O Babel é um ferramenta que é usada principalmente para converter o código ECMAScript 2015+ em uma versão compatível com versões anteriores do JavaScript em navegadores ou ambientes atuais e antigos.

podemos adicioná-lo ao nosso projeto com os comandos:
```
$ yarn add @babel/cli
$ yarn add @babel/preset-env
$ yarn add @babel/core
```

**IMPORTANTE: se você for utilizar algum controle de versão essa é o momento ideal pra criar seu .gitignore, adicionando a ele a pasta */node_modules***

Nosso próximo passo será criar alguns arquivos de configuração na raiz do nosso projeto. Podemos começar com o arquivo *.babelrc* que deve ter em seu conteúdo o seguinte código:

*.babelrc*
```json
{
    "presets": ["@babel/preset-env"]
}
```

E no arquivo *package.json* devemos adicionar o código para o script que vamos usar no terminal para que o Babel possa compilar nosso código de ES6+ para uma sintaxe que seja reconhecida em todos os navegadores atuais, adicionando o campo "scripts" com o seguinte valor:

*package.json*

```json
{
  "name": "projeto",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "dependencies": {
    "@babel/cli": "^7.4.3",
    "@babel/core": "^7.4.3",
    "@babel/preset-env": "^7.4.3"
  },
  "scripts": {
    "dev": "babel ./main.js -o ./bundle.js -w"
  }
}
```

Este código fará com que todo código ES6+ que for escrito no arquivo *main.js* seja transpilado para js comum no arquivo *bundle.js*. Sendo este último, o arquivo que devemos incluir no body do nosso arquivo HTML.

Por último devemos abrir um terminal de nossa preferência e digitar o comando:
```
$ yarn dev
```

E SHAZAM! 

A partir de agora o Babel ficará responsável por monitorar nosso código e transpilá-lo de acordo com nossas alterações.
