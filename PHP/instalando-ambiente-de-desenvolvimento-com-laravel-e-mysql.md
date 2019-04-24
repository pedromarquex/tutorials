<h1>Instalando ambiente de desenvolvimento web com PHP no Ubuntu</h1>
<h5>Escrito por <a href="https://github.com/filipeas">Filipe A.S</a></h5>

<p>Este tutorial tem como objetivo:</p>

<ul>
<li>Instalar php 7.3.*</li>
<li>Instalar MySQL 8</li>
<li>Instalar Composer</li>
<li>Instalar Laravel 5.7</li>
</ul>

<p>É importante observar cada detalhe no tutorial, pois estarei colocando todos os problemas que encontrei durante as instalações, e o que fiz pra contornar cada problema.</p>

<h3>1) Instalando php 7.3.*</h3>

<p>Adicione o repositório do PHP. Para instalar o PHP 7.3, você precisará usar um repositório de terceiros. Usaremos o repositório de Ondřej Surý que usamos anteriormente.</p>
<p>Primeiro, verifique se você tem o seguinte pacote instalado para poder adicionar repositórios:</p>
<pre>sudo apt-get install software-properties-common</pre>
<p>Em seguida, adicione o repositório PHP do Ondřej:</p>
<pre>sudo add-apt-repository ppa:ondrej/php</pre>
<p>E finalmente, atualize sua lista de pacotes:</p>
<pre>sudo apt-get update</pre>
<p>OBS: sempre realize os comandos acima como root</p>
<p>Depois de adicionar o repositório, você pode instalar o PHP 7.3 com o seguinte comando:
</p>
<pre>sudo apt-get install php7.3</pre>
<p>Pacotes adicionais mais usados:</p>
<pre>sudo apt-get install php-pear php7.3-curl php7.3-dev php7.3-gd php7.3-mbstring php7.3-zip php7.3-mysql php7.3-xml</pre>

<h3>Instalando MySQL</h3>

<p>Adicione o seguinte repositório, fazendo o download do arquivo:</p>
<pre> wget -c https://dev.mysql.com/get/mysql-apt-config_0.8.10-1_all.deb</pre>
<p>Em seguida, usando a ferramenta de pacote dpkg, instale o pacote de repositórios do MySQL como mostrado abaixo:</p>
<pre>dpkg -i mysql-apt-config_0.8.10-1_all.deb</pre>
<p>Depois de executar o comando acima, você obtém um prompt de exibição que fornece uma seleção de instâncias do MySQL que você pode escolher. Role para baixo e selecione a última opção - "Ok"</p>
<p>Em seguida, execute o comando abaixo para instalar a instância e o cliente do servidor MySQL, que é usado para efetuar o registro remotamente no servidor MySQL:</p>
<pre>sudo apt install mysql-server mysql-client</pre>
<p>Para confirmar que instalamos com sucesso o servidor MySQL e o cliente MySQL em nosso sistema, execute:</p>
<pre>dpkg -l | grep "mysql"</pre>
<p>Para fazer login no mysql:</p>
<pre>mysql -u root -p</pre>

<p>OBS: Tive problemas com o socket do mysql e com a parte de criação do usuário. Para mim, nunca aparece a tela de criar o root e a senha dele, daí acabo tendo um problema de autenticação lá no laravel, quando começarmos a programar. A solução veio desse <a href="http://www.leandrosales.com.br/2016/09/17/reset-root-password-no-mysql-5-7/"> tutorial</a>. Talvez eu copie todos os passos dele e coloque aqui pra facilitar, mas isso fica pra depois! pelo menos o link tá aí....</p>

<h3>Instalando Composer</h3>

<p>Atualize novamente seus pacotes:</p>
<pre>sudo apt-get update</pre>
<p>Instale o utilitário curl:</p>
<pre>sudo apt-get install curl</pre>
<p>Baixe o instalador:</p>
<pre>sudo curl -s https://getcomposer.org/installer | php</pre>
<p>Mova o composer.phararquivo:</p>
<pre>sudo mv composer.phar /usr/local/bin/composer</pre>
<p>Use o comando composer para testar a instalação. Se o Composer estiver instalado corretamente, o servidor responderá com uma longa lista de informações e comandos de ajuda:</p>
<pre>composer</pre>

<h3>Instalando Laravel</h3>

<p>Usando o composer, digite no terminal:</p>
<pre>composer global require "laravel/installer"</pre>
<p>Depois adicione a seguinte variável de ambiente:</p>
<pre>export PATH="~/.config/composer/vendor/bin:$PATH"</pre>
<p>OBS: Existe 3 locais para adicionar variáveis de ambiente no ubuntu. Eu coloquei o PATH do laravel em todas elas(utilize o nano ou outro editor de texto e coloque a variável de ambiente no final dos arquivos que estão citados logo abaixo). Estão abaixo listadas:</p>
<ul>
<li>/etc/profile</li>
<li>/etc/profile.d/</li>
<li>/etc/bash.bashrc</li>
</ul>
<p>Após isso, basta testar no terminal usando o comando:</p>
<pre>laravel -V</pre>

<h4>Fim!</h4>