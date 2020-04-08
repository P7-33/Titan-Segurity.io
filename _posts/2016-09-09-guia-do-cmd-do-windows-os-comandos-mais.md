---
title: 'Guia do CMD do Windows: os comandos mais úteis para operar o sistema na
linha de comando'
date: 2019-09-29T12:39:00+01:00
draft: false
---

  

===

 2.   Guia CMD do Windows: os comandos mais úteis ...

de software

[3](https://www.adslzone.net/esenciales/windows-10/comandos-CMD-consola/#disqus_thread) 

No sistema operacional Microsoft, inclui mais e mais opções, funções e configurações para que o usuário possa configurar, personalizar e gerenciar seu sistema como desejar. No entanto, embora para muitos usuários ainda seja um grande desconhecido, o Windows possui o que conhecemos como **prompt de comando ou CMD** . Não é nada além de uma linha de comando a partir da qual podemos fazer muitas das coisas que podemos fazer a partir da interface gráfica do sistema e até outras que não temos dessa maneira. Em seguida, mostraremos um **guia CMD com os comandos mais básicos e úteis** para começar a usar o console do Windows.

O que é o prompt de comando ou CMD e como abri-lo
-------------------------------------------------

**CMD** são as abreviações de CoMmanD e é um programa equivalente da Microsoft, command.com, o interpretador de comandos do MSDOS. Para que todos possam entendê-lo, é um tipo de tradutor de comandos que o próprio sistema usa para que possa interpretá-los e executá-los.

![](https://www.adslzone.net/app/uploads/2019/09/cmd0-715x412.jpg)

Os usuários para quem o prompt de comando é um grande desconhecido estarão se perguntando e onde está essa ferramenta ou programa? Bem, precisamos saber que, para abrir a janela do CMD ou do prompt de comando, basta digitar **"prompt de comando"** ou **"cmd"** na caixa da barra de pesquisa da barra de tarefas e clicar em no aplicativo na lista de resultados ou abra uma janela de execução do Windows, **Win + R,** digite " **cmd** " e pressione enter ou OK. De uma forma ou de outra, uma janela será aberta automaticamente com a linha de comando, onde podemos começar a escrever as ordens que queremos executar no sistema.

Às vezes, precisamos de permissões de administrador para executar alguma ação no sistema, algo que também pode acontecer conosco na linha de comando. Para executar o CMD ou o prompt de comando com **permissões de administrador** , digite "prompt de comando" ou "CMD" na caixa de pesquisa da barra de tarefas e, no resultado, clique com o botão direito do mouse mouse para selecionar a opção Executar como administrador.

CMD vs PowerShell
-----------------

O **CMD** , um prompt de comando ou também conhecido como **prompt de comando,** é um interpretador de linha de comando que acompanha o sistema operacional da Microsoft há décadas. Tanto que é o Shell original para o sistema operacional Microsoft DOS e o Shell padrão no Windows até a compilação 14791 do Windows 10, quando o Windows Powershell se tornou a opção padrão do sistema.

Com o prompt de comando, podemos **iniciar ou executar comandos básicos** , preparar scripts relativamente simples e executar muitas das tarefas que podemos executar na interface gráfica do sistema operacional Microsoft. Agora, quando precisamos fazer desenvolvimentos mais avançados, acessar determinadas áreas do sistema ou automatizar tarefas é onde o **Windows PowerShell** aparece **.**

![](https://www.adslzone.net/app/uploads/2019/09/cmdshell-715x264.jpg)

À medida que o Windows progredia e evoluía, a Microsoft também decidiu incorporar uma ferramenta mais moderna e poderosa ao CMD ou ao prompt de comando. E é que o Windows PowerShell é uma **linguagem de script e Shell avançada** escrita no Microsoft .NET Framework e à qual foram adicionados certos **cmdlets** que permitem executar **tarefas em segundo plano** ou **remotamente** , além da **automação de tarefas** . Uma ferramenta mais projetada para administradores de sistema e descrita como a substituição lógica pela passagem do tempo do CMD.

Conhecimento básico e comandos mais úteis do CMD
------------------------------------------------

Quando estivermos na frente da linha de comando do prompt de comando, devemos saber que existem certos comandos e chaves que nos ajudarão muito no uso do CMD, bem como para tirar o máximo proveito dele.

### Comandos básicos do CMD

#### Ajuda

O primeiro comando que devemos aprender é o comando Ajuda. Para executar este comando, basta digitar help na linha de comando e pressionar Enter. Automaticamente, veremos como vemos uma lista dos comandos básicos que podemos usar no console do sistema e para que servem cada um.

#### /?

Todos os comandos que executamos exigem que eles tenham uma sintaxe correta para serem executados sem problemas. Como não podemos memorizar cada uma dessas sintaxes, o próprio CMD oferece um comando para verificar a sintaxe do uso de qualquer comando. Para fazer isso, basta escrever o nome do comando, deixar um espaço e depois escrever os caracteres /? e pressione Enter. Por exemplo, se quisermos saber qual é a sintaxe correta para usar o comando cd, que veremos posteriormente para que serve, teremos que executar o cd /? Automaticamente, veremos como a sintaxe correta ou a sintaxe que nos permite usar esse comando aparece.

#### CD

Por padrão, o prompt de comando é aberto no caminho C: \\ Users \\ username, no entanto, talvez seja necessário percorrer outras pastas ou unidades do sistema para executar as tarefas apropriadas. Para fazer isso, usaremos o comando cd, que nos permite mover entre pastas. Para inserir uma pasta no caminho em que estamos, tudo o que precisamos fazer é executar o comando:

_cd foldername_

Para ir diretamente para uma pasta dentro desse caminho sem precisar passar pelas pastas anteriores, podemos executar:

_CD pasta1 \\ pasta2 \\ pasta3._

Se, por outro lado, queremos voltar, ou seja, deixar uma pasta e retornar à pasta que a contém, basta executar o comando cd .., enquanto que, se queremos sair imediatamente para a raiz da unidade em que estamos , então precisamos executar o **cd \\** .

#### Trocar unidade

Se tivermos várias partições ou unidades em nosso disco ou se houver um dispositivo de armazenamento interno conectado e quisermos acessar essa unidade no prompt de comando, basta escrever a letra dessa unidade seguida de dois pontos e pressionar Enter a partir do caminho onde são automaticamente e que unidade é seleccionada, por exemplo **e:** .

#### DIR

Quando estamos em um determinado caminho e queremos conhecer as pastas ou arquivos dentro dele, assim como podemos fazer a partir do gerenciador de arquivos na interface gráfica do Windows, o que precisamos fazer é executar o comando dir. Seremos automaticamente mostrados por linha de comando todas as pastas e arquivos contidos na pasta em que estamos. Para identificar o que é uma pasta e um arquivo, basta ver se

aparece na frente do nome, o que indica que é um diretório ou pasta. Se for um arquivo, o tamanho dele aparecerá à esquerda do nome.

![CMD](https://www.adslzone.net/app/uploads/2019/09/dir-715x413.jpg)

#### CLS

Com este comando, excluímos tudo o que aparece na linha de comando e ele fica completamente limpo, para que possamos começar novamente do zero. Simplesmente digite cls e pressione Enter.

#### EXIT

Se digitarmos o comando exit e pressionar Enter para executá-lo na linha de comando, veremos como a janela do CMD ou o prompt de comando se fecha automaticamente. E é que o comando exit é o que temos que usar para fechar o console.

![](https://www.adslzone.net/app/uploads/2019/09/cmd1-715x335.jpg)

### Comandos para gerenciar seus arquivos e pastas no prompt de comando

Na linha de comando, também podemos criar novas pastas e arquivos, excluí-los ou mover arquivos de um caminho para outro, como fazemos no explorador de arquivos do Windows.

#### MD

Se o que queremos é criar uma nova pasta ou diretório dentro de uma rota a partir da linha de comando, tudo o que precisamos fazer é ir para essa rota e, uma vez lá, executamos o comando:

_md foldername_

Tudo o que precisamos fazer é substituir o nome da pasta pelo nome que queremos atribuir ao novo diretório.

Se queremos criar um caminho de subpasta dentro de uma pasta, o comando é o mesmo, mas em vez de indicar o nome da pasta, teremos que escrever o caminho com o nome das subpastas. Por exemplo:

_md folder1 \\ folder2 \\ folder3_

#### RD

Para excluir uma pasta, a primeira coisa que precisamos fazer é garantir que o diretório esteja vazio, pois, nesse caso, não nos permitirá excluir a pasta. Quando a pasta estiver vazia, a partir do caminho que contém essa pasta, teremos que executar o comando:

_rd foldername_

#### COPY

Copiar é o comando que nos permite copiar arquivos, ou seja, copiar um arquivo de um diretório para outro. O comando a ser executado, se quisermos mover o arquivo1.ext para a pasta de testes no caminho em que estamos, **copie os arquivos do arquivo1.ext** . Agora, também podemos copiar o arquivo1.ext na pasta de testes, mas com outro nome arquivo2.ext, nesse caso, o comando a ser executado é:

_copiar arquivo1.ext testes \\ arquivo2.ext_

O comando copy também pode ser usado para criar um arquivo de texto em qualquer pasta do CMD. Para fazer isso, tudo o que precisamos fazer é escrever e executar o comando copy com filename.txt. Assim que pressionar a tecla Enter para executar o comando, o cursor permanecerá na linha abaixo e, em seguida, podemos começar a digitar o que queremos que o arquivo txt que vamos criar contenha. Para indicar que terminamos, pressione Ctrl + Z e pressione Enter e já podemos ver como, no caminho indicado, o arquivo de texto que criamos com o texto indicado já aparece.

![](https://www.adslzone.net/app/uploads/2019/09/copy-715x400.jpg)

#### XCOPY

Para copiar todos os arquivos de um diretório ou pasta para outro, usaremos o comando xcopy. Dessa forma, podemos executar:

_xcopy folder1 folder2_

Veremos como os arquivos da pasta1 são copiados para a pasta2. Se no final do comando adicionarmos o parâmetro / S, estaremos indicando que os diretórios e subdiretórios são copiados, exceto aqueles que estão vazios. Se adicionarmos o parâmetro / E, a cópia de todos será feita, incluindo as vazias.

#### MOVE

O comando move nos permite, como o nome indica, mover arquivos e pastas no CMD. A sintaxe deste comando nos permite mover arquivos de uma pasta para outra, incluindo uma pasta e seu conteúdo em outra pasta. Se o que queremos é mover um arquivo para outra pasta, passamos do prompt de comando para a pasta em que o arquivo que queremos mudar de local está localizado e executamos o comando move file.ext folder1. Se o destino estiver em uma rota diferente, podemos usar o comando da seguinte maneira:

_move file.ext c: \\ caminho de destino_

Mover também permite mover um arquivo para outro local e, ao mesmo tempo, renomeá-lo, o comando dessa vez seria:

_ mova file.ext C: \\ nome do caminho \\ newname.ext_

#### FSUTIL FILE CREATENEW

Para criar outro tipo de arquivo, por exemplo, um documento do Word, no prompt de comando, usaremos o comando fsutil file createnew da seguinte maneira.

_Arquivo fsutil cria novo C: \\ path \\ filename.ext NNN_

Onde C: \\ path deve ser substituído pelo caminho em que queremos criar o referido arquivo, filename.ext deve indicar seu nome e extensão e NNN o tamanho com o qual queremos criar o documento ou o tipo de arquivo do Word.

#### DEL

Para excluir ou excluir um arquivo, usaremos o. Para fazer isso, passamos para o caminho em que o arquivo está localizado e executamos:

_from filename.ext_

O arquivo será excluído automaticamente desse caminho.

#### REN

O comando ren nos permite renomear arquivos e pastas. Caso desejemos alterar o nome de um arquivo, passaremos pela pasta que o contém e executaremos:

_ren filename.ext newname.ext_

Para renomear uma pasta, o comando seria o mesmo, mas sem especificar a extensão:

_ren folder1 folder2_

![](https://www.adslzone.net/app/uploads/2019/09/ren-715x470.jpg)

#### ÁRVORE

Embora o comando dir mencionado acima nos mostre uma lista de tudo o que contém uma pasta, geralmente podemos ver a árvore de diretórios ou a árvore de diretórios e seu conteúdo no CMD ou no prompt de comando. Para fazer isso, podemos tirar proveito do comando **tree** que, se o executarmos, ele retornará a árvore de pastas abaixo do caminho em que estamos, mas que se a executarmos como tree / f, também nos mostrará todos os arquivos que cada um contém Diretórios em forma de árvore também.

![CMD](https://www.adslzone.net/app/uploads/2019/09/tree-715x413.jpg)

#### TIPO

Assim como podemos criar facilmente um arquivo de texto a partir da linha de comando, é possível ver seu conteúdo graças ao comando type. Para fazer isso, basta escrever:

_digite file.txt_

O conteúdo do arquivo de texto será exibido automaticamente no console. Este comando permite passar dois parâmetros, ou seja, dois arquivos de texto, para que possamos ver o conteúdo de dois arquivos executando um único comando:

_digite file1.txt file2.txt_

### Como criar, ativar e desativar usuários do Windows a partir do CMD

O fato de compartilhar o computador com outras pessoas torna necessário criar novas contas de usuário. Isso é algo que o próprio Windows nos permite fazer a partir da configuração do sistema, mas também podemos gerenciar nossas contas de usuário no prompt de comando ou CMD.

#### Usuário líquido

Usuário da rede é o comando que facilitará a tarefa de criar uma conta de usuário no sistema. Sua sintaxe é muito simples, mas sempre podemos verificá-la executando net user /?. No entanto, para criar uma nova conta de usuário, teremos que executar:

_net user Senha do Usuário / adicionar_

Onde Usuário e Senha, devemos substituí-lo pelo nome de usuário que queremos criar e a senha a ser usada.

Esse mesmo comando também permite ativar ou desativar uma conta de usuário, para isso usaremos o comando da seguinte maneira:

_net user Usuário / ativo: não_ ou _net user Usuário / ativo: sim_

### Comandos básicos de rede

Na linha de comando, também é possível acessar alguns recursos de rede, como nosso endereço IP, endereços DNS ou executar algumas tarefas bastante úteis em determinados momentos, como limpar o cache DNS, entre outros.

#### PING

Este comando permite conhecer o status da rede estabelecendo uma comunicação com um site, por exemplo, e verificando se a entrega de pacotes é bem-sucedida. Seu uso é muito simples, basta escrever ping seguido de um site, por exemplo, o Google, e verificar se os pacotes necessários são enviados e recebidos para estabelecer comunicação e navegar. Exemplo:

_ping www.google.es_

#### IPCONFIG

Ipconfig é o comando que nos permite conhecer as configurações atuais da rede TCP / IP, como o nome do adaptador ou da placa de rede usada na conexão, o endereço IP atribuído ao dispositivo, o endereço IP do dispositivo que funciona como servidor ou proxy e esse é o que tem acesso à Internet, bem como servidores DNS e status e configuração de DHCP. Para fazer isso, basta ir à linha de comando, digite **ipconfig** e pressione Enter.

![](https://www.adslzone.net/app/uploads/2019/09/ipconfig-696x500.jpg)

Este comando também nos permite limpar o cache do DNS se o usarmos da seguinte maneira, **ipconfig / flushdns** . Embora estas sejam outras opções também usadas com o comando ipconfig: **ipconfig / all** para exibir informações em nossa placa de rede, **ipconfig / release** libera o endereço IP do adaptador e **ipconfig / renew** renova o endereço IP do adaptador de rede.

#### TRACERT

Este comando permite conhecer exatamente a rota dos pacotes antes de chegar ao computador de destino, o que facilita a detecção de possíveis falhas de roteamento dos pacotes na conexão. Sua sintaxe também é muito simples, basta escrever o comando **tracert** seguido pelo site com o qual queremos verificar a rota ou o endereço IP do computador de destino.

#### NETSTAT

Também é possível monitorar o status da atividade de rede usando este comando, que permite ver o comportamento da rede facilmente e saber o número de conexões ativas no PC. A sintaxe do comando é muito simples, ao lado do comando podemos adicionar uma opção, o protocolo e o intervalo de tempo com o qual as conexões são monitoradas.

_Netstat \[opção\] \[-p protocol\] \[intervalo\]_

Estas seriam as opções a serem usadas:

\-a Mostra todas as conexões e portas para escutar.  
\-b Exibe os aplicativos e arquivos executáveis ​​responsáveis ​​pela criação de conexões nas portas de atendimento.  
\-e estatísticas de Ethernet.  
\-n Para exibir portas e endereços em formato numérico.  
\-o Mostra a identidade de cada processo.  
\-r Mostra a tabela de rotas.  
\-s Mostra estatísticas por protocolos.  
\-v Se o usarmos junto com -b, nos permitirá ver sequências de componentes responsáveis ​​pela criação da conexão.  
\-p Mostra as conexões por protocolos: TCP, UDP, TCPv6, etc.  
Intervalo, indicamos a cada poucos segundos que as conexões são monitoradas. Podemos forçar a conclusão do processo com o atalho de teclado Ctrl + C.

### Comandos para resolver alguns erros do sistema

Como encontramos alguns reparadores de bugs na interface gráfica do Windows, o sistema operacional da Microsoft possui outras ferramentas baseadas em comandos que nos permitem reparar ou solucionar determinados problemas do sistema.

#### DISM

Eles são o acrônimo de Serviço e Gerenciamento de Imagens de Implantação e se referem a uma ferramenta desenvolvida pela Microsoft com base em uma linha de comando que nos permite executar a manutenção e a preparação de imagens do sistema.

Os comandos do DISM nos permitem capturar e aplicar imagens do Windows, adicionar ou remover imagens de um arquivo .win ou até dividir arquivos .win em outros menores. Para executar uma análise de uma imagem do Windows para detectar erros ou arquivos corrompidos, podemos executar o comando:

_Dism / Online / Imagem de limpeza / ScanHealth_

Como sempre, podemos ver o restante das opções e parâmetros executando dism /?. Lembre-se de que, para usar a ferramenta DISM, teremos que abrir o prompt de comando ou o CMD com permissões de administrador.

#### CFS

Outro comando interessante a esse respeito é o SFC, que nos permite procurar arquivos de sistema danificados e, se encontrados, tentará automaticamente repará-los ou substituí-los. Seu uso é muito simples, basta abrir uma janela de prompt de comando com permissões de administrador e depois executar

_sfc / scannow_

Agora, basta aguardar a conclusão do processo, pois ele tentará reparar qualquer arquivo de sistema danificado automaticamente.

#### CHKDSK

Nesta ocasião, o comando chkdsk nos ajuda a detectar problemas em nosso disco rígido ou unidade de armazenamento do equipamento. Dessa maneira, executando a ferramenta na linha de comando, podemos detectar problemas em nosso disco para evitar erros graves. Seu uso é muito simples, basta escrever o comando **chkdsk,** seguido de **um espaço** e a **letra** da unidade **junto com: o** que corresponde à partição ou disco que queremos analisar. O comando admite uma série de parâmetros para indicar se queremos que, além de detectá-los, tente corrigir (/ F), se encontra setores defeituosos que tentam recuperar as informações (/ R), etc. Todos nós podemos vê-los executando o chkdsk /?.

![](https://www.adslzone.net/app/uploads/2019/06/apagarpc-715x374.jpg)

### Como desligar ou reiniciar o PC a partir do console

#### DESLIGAMENTO

Se quisermos desligar o equipamento no prompt de comando ou no CMD, Shutdown é o comando que devemos usar. Além disso, nos permite indicar se queremos que o desligamento seja imediato ou mesmo se queremos que ocorra após um tempo específico. Por exemplo, para desligar o PC automaticamente, basta digitar e executar o comando:

_desligamento / s / p_

Onde / s indica que o desligamento do sistema e / p devem ser executados imediatamente sem aguardar o tempo de comando padrão que é de cerca de 30 segundos.

Se, em vez disso, queremos que nosso PC seja desligado dentro de 1 hora, devemos executar o comando:

_desligamento / s / t 3600_

![](https://www.adslzone.net/app/uploads/2019/09/shutdown-715x469.jpg)

Onde 3600 são os segundos que você esperará para desligar. Podemos ver todas as opções de desligamento executando o desligamento /?. Se, para alguma coisa, quisermos cancelar o desligamento do equipamento programado pelo desligamento, teremos que executar o comando shutdown / a.

Para reiniciar o computador, teremos que usar esse mesmo comando, mas junto com o parâmetro / r. Se executarmos o comando:

_desligamento / r / t 60_

Nossa equipe será reiniciada em 60 segundos.

### Atalhos de teclado úteis no prompt de comando

Como quase qualquer ferramenta que vale a pena, o CMD ou o prompt de comando também nos permite usar certas combinações de teclas ou atalhos de teclado para executar determinadas tarefas rapidamente.

#### ESC

Quando estamos digitando um comando no prompt de comando e queremos excluí-lo, basta pressionar a tecla Escape no teclado e ele apagará tudo automaticamente, sem precisar caracterizar caractere.

#### Seta para cima e para baixo

As teclas com as setas para cima e para baixo do teclado permitem que, no CMD, percorra os comandos executados no console desde que o abrimos. Com o cursor de seta para cima, percorreremos os comandos executados anteriormente e, com a seta para baixo, retornaremos aos executados posteriormente.

#### F7

A tecla F7 mostra uma janela com o histórico de comandos usados ​​no prompt de comando. Dessa forma, podemos vê-los todos de uma vez e executá-los novamente, basta selecioná-lo e pressionar Enter.

#### Ctrl + c

Este atalho de teclado nos permite cancelar o processo em execução. Se, por exemplo, lançamos um comando que está demorando muito para ser executado e queremos cancelá-lo, podemos fazê-lo com Ctrl + c.

#### F11

F11 ativa o modo de tela cheia para que a janela do prompt de comando se torne grande e possamos trabalhar com mais conforto. Se a qualquer momento desejar diminuí-lo novamente, basta pressionar F11 novamente.

#### F3

A tecla F3 reescreve o último comando executado no CMD sem precisar redigitá-lo.

#### F1

F1 nos escreve novamente o último comando executado no prompt de comando, mas desta vez ele executa caractere por caractere a cada pressionamento da tecla F1.

Escrito por Roberto Adeva

29 de setembro de 2019 às 10:20

Fonte> ADSLZone