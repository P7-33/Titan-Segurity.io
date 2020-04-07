---
title: 'Guia para iniciantes de investigação OSINT com Maltego'
date: 2020-02-01T14:33:00+01:00
draft: false
---

![](https://miro.medium.com/max/1920/0*ItJwXaChewTJuxwb.JPG)
============================================================

Gráfico de atribuição entre um domínio e seus proprietários de ["); text-decoration-line: none;" target="\_blank">https://www.paterva.com](https://www.paterva.com/)

> Isenção de responsabilidade da Maltego: A empresa esclarece que o software não pode ser usado para ações ilegais: “Você não está limitado em como pode usar o software, mas não pode usá-lo para ações ilegais (incluindo a coleta de endereços de email para envio de spam). O mesmo vale para os dados ou gráficos que você gera usando-os. ”Eles também acrescentam:“ Você não pode nos culpar de forma alguma se algo der errado com este software. Se você usar este software e tiver problemas de alguma forma, é problema seu. ”

O que é o Maltego e por que usá-lo no OSINT?
============================================

O Maltego é uma ferramenta de mineração de dados que explora uma variedade de recursos de dados de código aberto e usa esses dados para criar gráficos para analisar conexões. Os gráficos permitem que você faça conexões facilmente entre informações como nome, estrutura organizacional de email, domínios, documentos etc. O Maltego usa Java para que possa ser executado no Windows, Mac e Linux e está disponível em muitas distribuições OSINT Linux como Buscador ou Kali. . Basicamente, ele analisa uma grande quantidade de informações e pesquisa em vários sites de código aberto para você e, em seguida, lança um gráfico bonito que o ajudará a juntar as peças. O Maltego pode ser usado como um recurso a qualquer momento durante a investigação; no entanto, se o seu destino for um domínio, faz sentido começar a mapear a rede com o Maltego desde o início.

![](https://miro.medium.com/max/60/0*8S7lLguFDAnsFX_G?q=20)

Esta imagem fará sentido no devido tempo (Decider.com)

Qual versão do Maltego devo baixar?
===================================

Existem várias versões do Maltego disponíveis:  
• Maltego XL - versão Premium para grandes dados  
• Maltego Classic - versão paga que inclui todas as APIs (transformações)  
• Maltego CE - versão gratuita com APIs limitadas (transformações)  
• Casefile - para examinar links em offline dados

> A principal diferença entre o Maltego Classic, o Maltego XL e o Maltego CE é o número de entidades que podem ser retornadas de uma única transformação e o número máximo de entidades que podem estar em um único gráfico.

Para nossos propósitos aqui, usarei o Maltego CE, que é uma versão gratuita com transformações limitadas. O Maltego vem pré-instalado na distribuição do Buscador Linux, que normalmente é o favorito dos investigadores de inteligência de código aberto.

![](https://miro.medium.com/max/60/0*CBW7ja77cewBZ4wk?q=20)

["); text-decoration-line: none;" target="\_blank">https://docs.maltego.com](https://docs.maltego.com/)

Instalando o Maltego
====================

Buscador: Se você possui o Maltego via Buscador, ele será apresentado inicialmente como a versão Casefile. Você precisará ir ao ["); text-decoration-line: none;" target="\_blank">Paterva](https://www.paterva.com/community/community.php) site e criar uma conta. Depois que sua conta for criada, você receberá uma chave que transformará seu Casefile em CE.

Kali: Maltego vem pré-instalado no Kali . Você precisará ir ao ["); text-decoration-line: none;" target="\_blank">Paterva](https://www.paterva.com/community/community.php) site e criar uma conta. Depois que sua conta for criada, você receberá uma chave que permitirá o uso da Community Edition.

Instalação nova: se você estiver fazendo uma nova instalação no Win, Mac ou Linux, aqui está uma["); text-decoration-line: none;" target="\_blank"> guia passo a passo](https://docs.maltego.com/support/solutions/articles/15000008704-installing-maltego) fornecido pela Paterva.

O que é todo esse absurdo de API / Transformação?
=================================================

![](https://miro.medium.com/max/60/1*zsErg825RyUFMA2Vz7el5A.png?q=20)

Captura de tela de transformações na versão do Windows

Uma API é uma interface de programação de aplicativos e, em termos muito simples, é o que conecta outros softwares como Shodan e Threatminer ao Maltego. O Maltego chama essas conexões de "Transformações" e, se você estiver executando o Maltego CE, verá que algumas transformações são gratuitas enquanto outras são pagas. A desvantagem de executar a versão gratuita do Maltego é que nem todas as transformações são pré-instaladas; portanto, para usá-las, você precisará se inscrever em cada site para obter o código da API para ativar a transformação correspondente. Dependendo das suas necessidades, você pode se concentrar em transformações específicas feitas para OSINT, Threat Intel, mapeamento de organização etc., que limitarão a quantidade de trabalho que você precisa fazer para a ativação.

Como executar um simples reconhecimento de rede
===============================================

Começando com um nome de domínio, podemos começar a mapear a estrutura de uma organização, incluindo outros sites de sua propriedade. É surpreendente quanta informação pode ser encontrada usando nada além de um nome de domínio.

Clique no botão novo gráfico no canto superior esquerdo e um novo painel de gráfico em branco será aberto.

![](https://miro.medium.com/max/60/1*81BGQ17QRDqD3O6d-hJbGw.png?q=20)

![](https://miro.medium.com/max/1365/1*81BGQ17QRDqD3O6d-hJbGw.png)

novo gráfico

Na Paleta de entidades à esquerda, role até encontrar Domínio e arraste-o para o painel de gráfico em branco.

![](https://miro.medium.com/max/60/1*UITNmxou-oCJ9PEIEJoSZw.png?q=20)

![](https://miro.medium.com/max/1389/1*UITNmxou-oCJ9PEIEJoSZw.png)

Localizar domínio na paleta de entidades

Clique duas vezes no ícone do domínio e altere o nome para o domínio que você deseja investigar. Eu escolhi hbo.com.

![](https://miro.medium.com/max/60/1*zGItBVHv642raF9yK-_lUw.png?q=20)

![](https://miro.medium.com/max/292/1*zGItBVHv642raF9yK-_lUw.png)

Clique com o botão direito do mouse no ícone do domínio , isso abre a caixa Executar transformações . Aqui você pode ser muito específico sobre o que deseja pesquisar, percorrendo a paleta e selecionando, mas vamos enlouquecer e basta escolher Executar todas as transformações selecionando as pequenas setas de avanço rápido ao lado.

![](https://miro.medium.com/max/60/1*5wxFbhEdhgB5skMVaqiDgQ.png?q=20)

![](https://miro.medium.com/max/1366/1*5wxFbhEdhgB5skMVaqiDgQ.png)

Executar todas as transformações no domínio

Assim que Run Transform é selecionado, Maltego começa seu trabalho fazendo um gráfico da estrutura da rede. Nota: no lado esquerdo do painel de gráficos, existem várias opções para visualizar o gráfico em diferentes layouts.

![](https://miro.medium.com/max/60/1*wYfwa7r-w5gx9ssD59Y86w.png?q=20)

Captura de tela do domínio hbo.com

Você pode ver na imagem abaixo que todo tipo de informação aparece, incluindo servidores DNS, sites relacionados, emails relacionados, servidores de email ...

![](https://miro.medium.com/max/60/1*sE7ZpbbOmhBb2_JWd3BGcQ.png?q=20)

Imagem mostrando a rede

Você pode usar essas conexões para fazer conexões ainda mais detalhadas, como nomes associados a emails e números de telefone.

![](https://miro.medium.com/max/60/1*nXj08GBnLqXwz1zWDRQpNg.png?q=20)

Vamos dar uma olhada em uma das pessoas que apareceram conectadas ao hbo.com “Thomas Peterson”. Clique com o botão direito do mouse no ícone de Thomas e execute Todas as transformações .

![](https://miro.medium.com/max/60/1*gTI0AWxCwSz3_dqaDEuJ6g.png?q=20)

Quando as transformações terminarem, teremos um gráfico adicional de todos os emails associados a Thomas Peterson.

![](https://miro.medium.com/max/60/1*_4kOMooazOOjNKJqUIVZBw.png?q=20)

![](https://miro.medium.com/max/923/1*_4kOMooazOOjNKJqUIVZBw.png)

Thomas Peterson's emails

Às vezes, isso pode levar a algumas descobertas estranhas. Eu me deparei com muitos e-mails engraçados / ocultos enquanto fazia pesquisas semelhantes.

![](https://miro.medium.com/max/60/1*sWX2ivLUOYyBeR5iN_TNpA.png?q=20)

![](https://miro.medium.com/max/670/1*sWX2ivLUOYyBeR5iN_TNpA.png)

Imagem das associações de email de Thomas Peterson

Como executar um endereço de email no Maltego
=============================================

Eu estava curioso sobre o endereço de Rick Grimes Tormail de Thomas, então decidi dar uma olhada mais de perto.

Crie um novo gráfico da mesma maneira que fizemos na etapa anterior. Dessa vez, selecione Endereço de email na paleta de entidades e arraste-o para o gráfico vazio.

![](https://miro.medium.com/max/36/1*AzC0CPEqqqeGuP1OOKmXXw.png?q=20)

![](https://miro.medium.com/max/423/1*AzC0CPEqqqeGuP1OOKmXXw.png)

Clique duas vezes no ícone do endereço de email e altere o texto para o endereço de email que você deseja pesquisar. Nesse caso, usei "realrickgrimes@tormail.org"

![](https://miro.medium.com/max/60/1*0JxOq0-qP2RRoBCpJshDVw.png?q=20)

![](https://miro.medium.com/max/255/1*0JxOq0-qP2RRoBCpJshDVw.png)

Clique com o botão direito do mouse no ícone do endereço de e-mail e execute Todas as Transformações selecionando as setas de avanço rápido.

![](https://miro.medium.com/max/60/1*2o3r1X8XzpEUZft6SW84gw.png?q=20)

![](https://miro.medium.com/max/1366/1*2o3r1X8XzpEUZft6SW84gw.png)

Captura de tela das transformações em execução em um endereço de email

Após a execução das transformações, um gráfico será exibido, exibindo todas as conexões com o endereço. Você pode ver aqui que realrickgrimes@tormail.org se conecta a uma pessoa “Rick Grimes”, que se conecta a vários outros e-mails. Fiquei intrigado com a conexão de Rick com carl.grimes1995@gmail.com, então decidi executar outras transformações no email.

![](https://miro.medium.com/max/60/1*cACXvjndFuL8Ck7Ld80c-g.png?q=20)

![](https://miro.medium.com/max/646/1*cACXvjndFuL8Ck7Ld80c-g.png)

Executando todas as transformações no endereço de email

Carl.grimes1995@gmail.com me levou a várias pessoas mais interessantes como Carl Grimes e Steve Brule. Eu sinto que estou sendo sugado para um buraco negro de referências de Walking Dead, então eu corro um Transform em Steve Brule.

![](https://miro.medium.com/max/60/0*qTQq-C7TuyHLsqtD?q=20)

![](https://miro.medium.com/max/700/0*qTQq-C7TuyHLsqtD)

me.me

![](https://miro.medium.com/max/60/1*0NvTPcuhWHFX1rg4crjX9w.png?q=20)

![](https://miro.medium.com/max/499/1*0NvTPcuhWHFX1rg4crjX9w.png)

Steve Brule me leva a steve@checkitout.com e steve@brule.com, além do site checkitout.com.

![](https://miro.medium.com/max/52/1*4KV88a9xWBY_523WFh4G4g.png?q=20)

![](https://miro.medium.com/max/437/1*4KV88a9xWBY_523WFh4G4g.png)

Tentei visitar o site, mas ele não estava ativo, então fiz uma ["); text-decoration-line: none;" target="\_blank">pesquisa](https://who.is/) rápida sobre o ["); text-decoration-line: none;" target="\_blank">WhoIs](https://who.is/) . A pesquisa WhoIs voltou registrada na CSC Global, que administra uma empresa de serviços de marca digital e de gerenciamento de domínio.

![](https://miro.medium.com/max/60/1*L0W0D_ECXgiU3U2DpeuZsw.png?q=20)

![](https://miro.medium.com/max/810/1*L0W0D_ECXgiU3U2DpeuZsw.png)

O registrante anterior era a Hearst Corporation

![](https://miro.medium.com/max/60/1*7gmacD0ZDnKEoA9StH8CCA.png?q=20)

![](https://miro.medium.com/max/498/1*7gmacD0ZDnKEoA9StH8CCA.png)

Neste ponto, em vez de continuar pela toca do coelho de Steve Brule, assumirei a organização Hearst e agora a CSC está mantendo o domínio para protegê-lo contra uso indevido ou revendê-lo em algum momento.

Como você pode ver, há um milhão de coisas divertidas que você pode fazer com apenas uma simples pesquisa de domínio e email no Maltego! Teste você mesmo o Maltego pesquisando seu próprio endereço de e-mail ou endereço da web e veja quais conexões você pode fazer. Dê um passo adiante e tente pesquisar pelo seu número de telefone para ver como ele pode ser vinculado a você.

Confira meu ["); text-decoration-line: none;" target="\_blank">tutorial para Lampyre](https://medium.com/@raebaker/using-lampyre-for-basic-email-and-phone-number-osint-e0e36c710880) se você estiver procurando outra solução baseada no Windows para reconhecimento de endereço de e-mail e gráficos.