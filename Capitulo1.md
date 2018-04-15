# Introdução ao Shell do Linux

## Abrir o terminal

Há vários jeitos de abrir um terminal na interface gráfica. Mas, se você está numa distribuição Debian basta apertar **ctrl+alt+t**.

Se conseguir abrir, vai aparecer um console como na imagem abaixo.
![terminal](https://github.com/josuegrace05/Code/blob/master/terminal.png)

A partir de agora nós vamos apresentar o texto que aparece no terminal no seguinte formato:

>josuegrace@josuegracestudy:~$

Você ainda não escreveu nada porém, o computador já fala bom-dia para você do seu jeito. O que você está vendo é o que se chama de **prompt de comando**. É uma mensagem que convida você a inserir um comando. Ele sempre aparece antes de você digitar um comando.

Agora, analisemos mais um pouco esse prompt de comando pois ele é muito interressante:

* josuegrace: esse é o seu nome de usúario. É o pseudônimo no qual você está logado. Com efeito, lembrem-se: é possível criar várias contas de usuário no Linux. É geralmente aconselhado gerar uma conta por cada pessoa que vai usar o computador (um por cada membro da família, por exemplo). Nós veremos mais tarde como adicionar contas de usúarios.

* @ : esse símbolo não indica nada em particular. É o símbolo "at" que significa "em". Assim, se ler o prompt de comando da esquerda para direita, devemos então entender "josuegrace em".

* josuegracestudy: esse é o nome do computador que você está usando. No meu caso ele se chama **josuegracestudy**, porém eu poderia dar um outro nome qualquer durante a instalação.

* :: esse símbolo não tem nada de especial. É apenas um separador.

* ~: esse símbolo é a pasta na qual você está atualmente. Você pode navegar de pasta em pasta dentro do console e é muito útil que lembre sistematicamente para você onde você está antes de cada comando.

O símbolo **~** significa que você está na sua pasta pessoal, o qual geralmente chamamos de "home" no Linux; é o equivalente da pasta "Meus documentos" do Windows. Nós estudaremos com mais detalhes o funcionamento das pastas no Linux no próximo capítulo.

* $: esse último símbolo é muito importante; ele indica o seu nível de autorização na máquina. Ele pode tomar duas formas diferentes:
	
	* $: significa que você está como um usuário "normal", com direitos limitados (ele não pode modificar os arquivos mais importantes do sistema). A minha conta **josuegrace** é então uma conta normal com direitos limitados;

	* #: significa que você está em modo *superusuário*, isso quer dizer que você está conectado sob o pseudônimo "root". O root é o usúario mestre que tem o direito de fazer tudo na sua máquina (até mesmo de destruî-la!). Nós veremos esse modo mais em detalhes mais tarde; por enquanto nós ficamos com a conta de usúario limitada, assim não arriscamos fazer besteiras.

Em resumo, uma vez que você fala a mesma língua que o prompt de comandos, você entende o que ele quer dizer: "Bom dia e bem-vindo, você é *josuegrace* na máquina *josuegracestudy*. Você está atualmente na sua pasta *home* e possui direitos de usúario limitados." :).

## Comandos e parâmetros

Dentro do console, trabalhamos com o que chamamos de **comandos**. Estes sendo ínumeros e você não consegue conhecer todos e não é esse o objetivo. O obejtivo é que você saiba de cor como usar a maiora dos comandos "comuns" e, para os menos comuns, que você seja capaz de aprender a usar lendo o manual de uso.

O manual de uso é **a verdadeira bíblia para usúarios de Linux**. Porque é simplesmente uma ferramenta de referência, ali podemos encontrar a resposta para TODAS suas perguntas sabendo como ler o manual.

Teremos um capítulo interio sobre como ler o manual: é realmente muito importante.

#### Um comando simples

> josuegrace@josuegracestudy:~$ date
	
	Qui Fev 22 16:13:20 -03 2018

A primeira linha contém o prompt de comando seguida do comando que eu digitei. A segunda linha é a resposta do computador para este comando.
Nesta linha, como vocês entenderam, nós pedimos quais eram a data e a hora.

Vamos tentar um outro comando: digite `ls`. É a breviação de "list", o que significa "**liste os arquivos e pastas do repertório atual**".

> josuegrace@josuegracestudy:~$ ls	
	
	Desktop Examples Images

Isso significa que o repertório atual contém 3 pastas: Desktop, Examples, Images. Em geral, o sistema colora todos os elementos para que possamos distinguir facilmente os arquivos das pastas.

Se não tiver resposta, quer dizer você que está numa pasta vazia.

É isso aí, tão simples assim. Um comando é constituido por uma palavra e não contém nenhum espaço. Nos casos simples como os que acabamos de ver, basta apenas digitar um comando para obter uma resposta; porém, na quase totalidade dos casos podemos (e as vezes devemos) digitar opções, que chamamos de **parâmetros**.

#### Os parâmetros

parâmetros são opções que escrevemos na frente do prompt de comando. O comando e os parâmetros são separados por um espaço, assim :

> josuegrace@josugracestudy: ~$ comando parâmetros

Os prórios parâmetros podem conter espaços, letras, números... um pouco de tudo, na verdade. Não há uma verdadeira regra sobre a forma dos parâmetros; porém, e felizmente os programadores estabeleceram uma "convenção" para que possamos reconhecer diferentes tipos de parâmetros.

#### Os parâmetros curtos (uma letra)

Os parâmetros mais comuns são constiuídos de uma letra precedida por um traço. Por exemplo:
> comando -d

Se devemos dar vários parâmetros, podemos fazer assim:
> comando -d -a -U -h

Ou mais curto:
> comando -daUh

> Atenção! "-u" em miníscula pode na maiora de casos não ter o mesmo sentido que "-U" em maíuscula.

Um exemplo com o comando `ls` junto com o parâmetro *a* (minúsculo):

> josuegrace@josugracestudy: ~$ ls -a

	.              .gconfd            .mozilla-thunderbird
	..             .gimp-2.2          .nautilus
	.bash_history  .gksu.lock         .profile
	.bash_logout   .gnome             .recently-used
	.bashrc        .gnome2            .recently-used.xbel
	.config        .gnome2_private    .ssh
	Desktop        .gstreamer-0.10    .sudo_as_admin_successful
	.dmrc          .gtkrc-1.2-gnome2  .themes
	.esd_auth      .ICEauthority      .thumbnails
	.evolution     .icons             .Trash
	Examples       .lesshst           tutos
	.face          .local             .update-manager-core
	.fontconfig    .macromedia        .update-notifier
	.gaim          .metacity          .Xauthority
	.gconf         .mozilla           .xsession-errors

Isto mostra todo o conteúdo da pasta, mesmo os arquivos escondidos.
Um "arquivo escondido" no Linux é um arquivo que começa por um ponto. Normalmente, se você está no repertório *home*, você deveria ter uma grande quantidade de arquivos escondidos. São em geral arquivos de configuração de programas.

#### Os parâmetros longos (várias letras)

Os parâmetros com várias letras são precedidos de dois traços, assim:
>comando --parâmetro

Desta vez, não tem escolha: se você quer colocar vários parâmetros longos, você deverá colocar um espaço entre eles:
>comando --parâmetro1 --parâmetro2

Pode também combinar os parâmetros longos e os parâmetros curtos dentro de um comando:
> comando -daUh --outroparametro

> Existe às vezes duas escritas possíveis para um parâmetro de comando: uma versão curta e uma versão longa. Isto permite deixar a escolha segundo o que você prefere entre um ou o outro.

Testemos isso com o comando ls junto com o parâmetro **--all**, que siginifica tudo em inglês:
>josuegrace@josuegracestudy:~$ ls --all

	.              .gconfd            .mozilla-thunderbird
	..             .gimp-2.2          .nautilus
	.bash_history  .gksu.lock         .profile
	.bash_logout   .gnome             .recently-used
	.bashrc        .gnome2            .recently-used.xbel
	.config        .gnome2_private    .ssh
	Desktop        .gstreamer-0.10    .sudo_as_admin_successful
	.dmrc          .gtkrc-1.2-gnome2  .themes
	.esd_auth      .ICEauthority      .thumbnails
	.evolution     .icons             .Trash
	Examples       .lesshst           tutos
	.face          .local             .update-manager-core
	.fontconfig    .macromedia        .update-notifier
	.gaim          .metacity          .Xauthority
	.gconf         .mozilla           .xsession-errors

Como você pôde notar, --all é sinônimo de -a.

#### Os valores dos parâmetros

Certos parâmetros necessitam que você os complete com um valor. Isto funciona diferentemente segundo que você está trabalhando com um parâmetro longo ou um parâmetro curto.

Com um parâmetro curto:
> comando -p 14

Isso indica que associamos o valor 14 ao parâmetro p. Com essa técnica, podemos por exemplo fazer o computador entender: "Eu quero ver a lista de todos os arquivos com 14 Mb".

Se é um parâmetro longo, em geral é assim:
> comando --parametro=14

Isso tem o mesmo resultado, porém é mais claro e mais longo para escrever.

#### Os outros parâmetros

Como nós dizemos mais cedo: não há uma regra absoluta no nível dos parâmetros e vocês encontrarão com certeza uns que funcionam diferentemente. Felizmente, as "convenções" que acabamos de dar são válidas na maioria dos casos.

Certos parâmetros são um pouco diferentes e dependem dos comandos. Por exemplo o comando `ls`, se digitarmos o nome de uma pasta (ou subpasta). isto mostrará o conteúdo dessa pasta em vez do contéudo da pasta corrente.

> josuegrace@josuegracestudy:~$ ls Examples
	
	Experience ubuntu.ogg   logo-Ubuntu.png           oo-payment-schedule.ods
	fables_01_01_aesop.spx  oo-about-these-files.odt  oo-presenting-kubuntu.odp
	gimp-ubuntu-splash.xcf  oo-about-ubuntu-ru.rtf    oo-presenting-ubuntu.odp
	kubuntu-leaflet.png     oo-cd-cover.odg           oo-trig.xls
	logo-Edubuntu.png       oo-derivatives.doc        oo-welcome.odt
	logo-Kubuntu.png        oo-maxwell.odt            ubuntu Sax.ogg

## Achar um comando

O Linux possui tantos comandos diferentes que é difícil de se perder e de esquecer algumas. Mas, isso não é um problema pois o Linux propõe uma série de formas de achar comandos que você esqueceu.

#### Autocomplete de comando

A primeira coisa a saber é o autocomplete de comando. Tomamos por exemplo o comando `date`: você não lembra mais como se escreve porém, você lembra das primeiras letras do comando.

Basta digitar "`da`" no console, e digitar duas vezes na tecla **Tab** na esquerda do seu teclado. E o resultado é o seguinte:
> josuegrace@josuegracestudy:~$ da
	
	dash date

> josuegrace@josuegracestdy:~$ da

Quando aperta duas vezes na tecla **Tab**, você está pedindo ao computador a lista dos comandos que començam por "*da*". E ele responde "*dash*" e "*date*". Há portanto dois comandos que començam por "*da*", e você acabou de achar aquela que você estava procurando, ou seja, "*date*".

O mais interessante ainda é quando só há um resultado na sua busca, o computador preencherá com as letras que faltam e você só terá de apertar no *Enter*!.

Às vezes há muitos comandos que correspondem à sua pesquisa. Por exemplo, se você não digitar nada e só apertar duas vezes *Tab*. Vai pedir para monstar a lista de todos os comandos disponíveis no seu computador.
> josuegrace@josuegracestdy:~$
	
	Display all 2173 possibilities? (y or n)

Muito brutal, não é ?
Há 2 173 comandos disponíveis no meu computador. Quanto nais eu instalar programas, mais terei comandos disponíveis. Não esperem então conhecer todos eles, novos programas saem todo dia.

Nesta pergunta, você pode responder "**y**" (yes) e a lista vai aparecer página por página. Alguns atalhos a saber quando uma lista aparece página por página:

* aperte *Espaço* para ir na página seguinte;
* aperte *Entrar* para ir na linha seguinte;
* aperte *q* para sair da lista.

Se você responder "**n**" (no), nada vai acontecer.

#### Histórico dos comandos

Muitas vezes necessitamos achar um comando que já digitamos há alguns minutos (ou mesmo segundos) atrás. Às vezes, é porque nós esquecemos o comando ou pode ser porque não queremos reescrever o comando inteiro de novo.

Esse atalho vale ouro: aperte a tecla com a flecha em direção para cima; você verá reaparecer o último comando que entrou. Se você digitar de novo a mesma tecla, aparecerá o penúltimo comando que entrou, e depois o que entrou antes do penúltimo, assim por diante.

Se você apertar a tecla com flecha em direção para baixo, vão aparecer os comandos mais recentes.

Se quiser voltar mais longe no histórico dos comandos, nem precisa apertar cem vezes na tecla "para cima". Existe o comando **`history`** que mostsra o histórico dos comandos.
>	
	152  date
	153  ls
	154  ls -a
	155  ls --all
	156  history

O último comando sempre vai ser *history*. Você vai notar que os comandos são numerados; assim, você pode saber que `date` é o 152o comando que entrei no terminal.

**Ctrl + R**: busca um comando com algumas letras.

No caso em que a tecla "para cima" e o comando `history` não bastam para achar uma velho comando que eu já digitei; há um atalho muito útil:
*ctrl +R*. Aperte então nas teclas *Ctrl* e *R* ao mesmo tempo e o computador se colocará em modo "busca de um comado digitado". Você então pode digitar qualquer série de letras de um velho comando. Por exemplo, digite "*Ctrl + R*" e depois digite "*all*". O Linux vai achar o comando "`ls --all`" que contém justamente a palavra "*all*". Agora é só digitar *Enter* para entrar novamente o comando.
> (reverse-i-search)'all': ls --all

Se não é o comando que está procurando, aperte novamente "*Ctrl + R*" para subir na lista de comandos que contêm "*all*".

## Alguns atalhos práticos do teclado.

Não pode parecer porém, o console do Linux propõe uma quantidade incrível de atalhos de teclado. Isto ajuda a ir muito rápido no que estamos fazendo.

Aqui está uma lista de alguns deles que você deve saber.

* **Ctrl + L**: Apaga o conteúdo do console. Muito útil para limpar o console quando ele está cheio. Existe também o comando *clear* que faz exatamente a mesma coisa.

* **Ctrl + D**: envia a mensagem de *EOF* (fim de arquivo) para o console. Se você apertar este atalho numa linha de comando vazia, isto fechará o console em uso. Existe também o comando `exit` que tem o mesmo efeito.

* **Shift + PgUp**: permite subir nas mensagens enviadas para o console. Em modo gráfico, é possível também fazer isso com o mouse.
* **Shift + PgDown**: A mesma coisa porém, para descer.

Os atalhos a seguir são úteis quando você está digitando um longo comando.

* **Ctrl + A**: coloca o cursor no começo do comando. A tecla *home* tem o mesmo efeito.
* **Ctrl + E**: coloca o cursor no final do comando. A tecla *end* tem o mesmo efeito.
* **Ctrl + U**: Apaga tudo que está a esquerda do cursor. Se o cursor estiver no final do comando, este será então apagado.
* **Ctrl + K**: Apaga tudo que está a direita do cursor. Se o cursor estiver no começo do comando, este será então apagado.
* **Ctrl + W**: apaga a primeira palavra  que está a esquerda do cursor. Uma palvara é separada por espaços; se usa geralmente para apagar o parâmetro que está a esquerda do cursor.
* **Ctrl + Y**: Se você apagou um texto com um dos comandos acima *Ctrl + U*, *Ctrl + K* ou *Ctrl + W*, então o atalho *Ctrl +Y* vai colar o dito texto que foi deletado.

Esta lista vai parar aqui. Já são bastante coisas para decorar. Outros atalhos vamos descobrir ao longo do curso.

Aconselhamos que treine para os decorar. Isto tornará você mais eficaz!
