# Usuários e Permissões
 
No Linux é possível realizar o gerenciamento de usuários, grupos e permissões de acesso via prompt de comando, veremos alguns dos principais comandos a seguir:
 
Os dois comandos mais básicos são o "**adduser**" e o "**passwd**", que permitem, respectivamente adicionar novos usuários e alterar as senhas de acesso posteriormente, como em:
 
**adduser _opções usuário_**
Adiciona um usuário ao sistema, é possível definir alguns parâmetros a partir das opções se desejar;
 
**adduser -disabled-login _usuário_** faz com que a conta do usuário seja criada sem a solicitação de uma senha (ou seja, não executa o comando **passwd**). No entanto, a conta não poderá ser usada até que o usuário defina sua senha de acesso;
 
**adduser -group _grupo_**: com esse parâmetro, ao invés de uma conta de usuário, um grupo é criado. Para essa tarefa também pode-se utilizar o comando **addgroup**;
 
**userdel voldmort**
Comando utilizado para apagar um usuário do sistema.
 
**userdel -r voldemort**
A opção **-r** do comando indica que além do usuário ser removido do sistema a sua pasta home também será deletada.
 
**passwd opções joao**
Caso um usuário queria alterar a sua própria senha, basta digitar apenas **passwd** em um terminal. O usuário root (ou outro que tenha privilégios de administrador) pode mudar não só a sua própria senha como a senha de todos os outros usuários do sistema. Para isso, o comando **passwd** também é usado e pode ser acrescido de opções.
 
Para alterar o shell do usuário você usa o parâmetro "-s", como em:
**usermod -s /usr/bin/rssh manuel**
 
Para alterar o home, você usa o parâmetro "-d", como em:
**usermod -d /var/www/manuel manuel**
 
Você pode também especificar estes parâmetros diretamente ao criar o usuário, como em:
**adduser --home /var/www/manuel --shell /usr/bin/rssh manuel**
 
Uma forma simples fazer isso é criar um grupo, adicionar os três usuários ao grupo e ajustar as permissões da pasta de forma que o grupo tenha permissão de escrita. Para adicionar o grupo, usamos o comando "**groupadd**", como em:
**groupadd intranet**
 
Para adicionar os usuários desejados ao grupo, usamos o próprio comando "**adduser**", seguido pelo login e o grupo ao qual ele deve ser adicionado (um de cada vez), como em:
**adduser maria intranet**
 
**Fontes:**
        https://www.hardware.com.br/tutoriais/usuarios-grupos-permissoes/
        https://www.infowester.com/usuarioslinux.php

# chmod: modificar as permissões de acesso

### O funcionamento das permissões

Cada arquivo e cada pasta possui uma lista de permissões. A lista indica quem tem a permissão de ver um arquivo, modificá-lo e executá-lo.
Digite no terminal o comando `ls -l` e dê uma olhada na prmeira coluna.

	joesuegrace@josuegracestudy:~$ ls -l
	total 40
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-11-13 21:53 Desktop
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-11-13 13:46 Documents
	lrwxrwxrwx 1 mateo21 mateo21   26 2007-09-19 18:31 Examples -> /usr/share/example-content
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-09-25 20:28 images
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-10-19 01:21 Images
	drwxr-xr-x 3 mateo21 mateo21 4096 2007-09-25 11:11 log
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-10-19 01:21 Modèles
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-10-19 01:21 Musique
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-10-19 01:21 Public
	-rw-r--r-- 1 mateo21 mateo21    0 2007-11-15 23:14 rapport.txt
	drwxr-xr-x 3 mateo21 mateo21 4096 2007-09-19 19:51 tutos
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-10-19 01:21 Vidéos

Os símbolos `d`, `r`, `w`e `x`são as ditas permissões dos arquivos e das pastas.
* **d** (Directory): indica se o elemento é uma pasta.
* **l** (Link): indica se o elemento é um atalho.
* **r** (Read): indica se o elemento pode ser lido.
* **w** (Write): indica se o elemento pode sr modificado.
* **x** (execute): indica se o elemento pode ser executado. É somente útil para arquivos executáveis como programas e scripts. Se o elemento é uma pasta, `x`indica que ela pode ser "transpassada" quer dizer que é possível ver as sub-pastas dentro dela se você tiver a permissão de leitura.

Se a letra aparecer isto quer dizer que a permissão existe. Porém, se tiver um traço no lugar quer dizer que não tem a permissão.

> Porque que às vezes tem `r`, `w`, e `x`repetidos ?

As permissões são divididas em grupo de utilizadores como segue:
![users](https://github.com/josuegrace05/AulasBashLinux/blob/master/users_permisions.jpeg)
* O primeiro conjunto de permissão `rwx`indica as permissões que possui o **dono** do arquivo;
* O segundo conjunto `rwx`inidica as permissões que possuem os outros membros do **grupo** sobre o  arquivo;
* E o último conjunto `rwx`indica as permissões que possuem os **outros** usuários da máquina sobre o arquivo.

####  `chmod`: modificar as permissões 

Agora que podemos ver e entender as permissões de acesso de um arquivo, agora vamos aprender a modificá-los via o comando `chmod`. 
Uma coisa importante para começar: diferentemente dos outros comandos, não é necessário ser root para utilisar o comando `chmod. Você apenas precisa ser dono do arquivo que quer modificar.

Há várias maneiras de modificar as permissões via `chmod` (absoluto), a maneira mais comum é usando números.

| Permissão | Número |
| --------- |:-------|
| r         |   4    |
| w         |   2    |
| x         | 1      |

Se quiser então combinar as permissões, vai ter que adicionar os números correspondentes. Assim, para attribuir a permissão de leitura e de modifcação, tem que adicionar $4 +2$, o que dá 6. O número siginifica então "permissão de leitura e de escrita".

| Permissão | Número | Addição |
| ------------ | :---------: | ----:| 
| - - - | 0 | 0 + 0 + 0 |
| r- - | 4 | 4 + 0 + 0 |
|- w - | 2 | 0 + 2 + 0 |
| - - x| 1 | 0 + 0 + 1|
| rw - | 6 | 4 + 2 + 0 |
| - wx | 3 | 0 + 2 + 1 |
| r - x | 5 | 4 + 0 + 1 |
|rwx | 7 | 4 + 2 + 1 |

Pode-se também usar letras com `chomod` (relativo).
Nesse modo tem que saber o seguinte:
* **u** = user (dono);
* **g** = group (grupo);
* ** o** = other (outros).

.... e :
* **+** siinifica: "Adicionar a permissão";
* **-** significa : "Tirar a permissão";
* **=** significa: "Afetar a permissão".

Por exemplo:

		chmod g+w rapport.txt
Significa: "Adicionar a permissão de escrita para o grupo".
		
		chmod o-r rapport.txt
Significa: "Tirar a permissão de leitura para o grupo".
	
		chmod u+rx rapport.txt		
Significa: "Adicionar a permissão de leitura e de execução para o dono".
	
	chmod g+w,o-w rapport.txt
Significa: "Adicionar a permissão de escrita para o grupo e tirar para os outros".

	chmod u=rwx,g=r,o=- rapport.txt
Significa: "Afetar todas as  permissôes para o dono, só a de leitura para o grupo, e nada para os outros".

 Existe também o parâmetro `-R`para modificar recursivamente
Se você modificar  as permissões sobre uma pasta com `-R`, todos os arquivos e as sub-pastas ficarão com as mesmas permissões.

Por exemplo, se eu quiser ser o único a poder ler, editar e executar os arquivos de meu repertório pessoal e de todos os arquivos, é só digitar o seguinte comando:

	chmod -R 700 /home/josuegrace
	
