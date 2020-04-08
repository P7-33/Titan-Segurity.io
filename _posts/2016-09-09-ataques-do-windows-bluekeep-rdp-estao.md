---
title: 'Ataques do Windows BlueKeep RDP estão aqui, infectando com mineradores'
date: 2019-11-04T01:14:00+01:00
draft: false
---

Por 

###### [Ionut Ilascu](https://www.bleepingcomputer.com/author/ionut-ilascu/)

 

*   2 de novembro de 2019
 *   22:26
 *   [0 0](https://www.bleepingcomputer.com/news/security/windows-bluekeep-rdp-attacks-are-here-infecting-with-miners/#comment_form)

  

![](https://www.bleepstatic.com/content/posts/2019/11/02/BlueKeepExploit_.png)

A vulnerabilidade de execução remota de código BlueKeep nos Serviços de Área de Trabalho Remota do Windows é atualmente explorada em estado selvagem. Máquinas vulneráveis ​​expostas à Web estão aparentemente comprometidas para fins de mineração de criptomoedas.

As tentativas foram registradas por honeypots que expõem apenas a porta 3389, específica para conexões de assistência remota por meio do Remote Desktop Protocol (RDP).

Ataques não são desagradáveis
-----------------------------

O pesquisador de segurança Kevin Beaumont notou no sábado que vários honeypots em sua rede de honeypot EternalPot RDP começaram a travar e reiniciar. Eles estão ativos há quase meio ano e é a primeira vez que eles desistem. Por alguma razão, as máquinas na Austrália não bateram, observou o pesquisador em um [tweet](https://twitter.com/GossiTheDog/status/1190656348700258310?s=20) .

[![](https://i.connatix.com/s3/connatix-uploads/0bbdd08f-296c-42e0-87be-83c87fcb5785/1.jpg?mode=crop&width=1001&height=563)ARTIGOS PRINCIPAIS1/5CONSULTE MAIS INFORMAÇÃOAtaques do Windows BlueKeep RDP estão aqui, infectando com mineradores![](https://www.bleepstatic.com/logos/bleeping-computerlogo-lg.png)

![](https://i.connatix.com/s3/connatix-uploads/af391ba1-47b0-4ff1-87cb-08a6df11845f/311.jpg?mode=stretch&connatiximg=true&scale=both&height=469&width=834)](https://www.blogger.com/null)

Os primeiros detalhes sobre o BlueKeep ser a causa desses eventos vieram da [MalwareTech](https://twitter.com/MalwareTechBlog) , que investigou os despejos de memória das máquinas de Beaumont. Ele disse que "encontrou artefatos BlueKeep na memória e no código de shell para soltar um Monero Miner".

![](https://www.bleepstatic.com/images/news/u/1100723/BlueKeepExploit_tweet-MalwareTech.png)

fonte: [MalwareTech](https://twitter.com/malwaretechblog/status/1190730471321112577)

De acordo com a análise inicial da MalwareTech, uma carga útil inicial executa um comando do PowerShell codificado que baixa um segundo script do PowerShell, também codificado. O pesquisador diz que a carga útil final é um minerador de criptomoeda, provavelmente para Monero, atualmente [detectado](https://www.virustotal.com/gui/file/8a87a1261603af4d976faa57e49ebdd8fd8317e9dd13bd36ff2599d1031f53ce/detection) por 25 dos 68 mecanismos antivírus na plataforma de varredura VirtusTotal.

Conversando com o BleepingComputer, o pesquisador disse que o malware pode não ser um worm, mas está explorando em massa o bug do BlueKeep. Isso indica que os cibercriminosos estão usando um scanner BlueKeep para encontrar sistemas vulneráveis ​​expostos na Web e soltar o minerador de criptomoedas neles.

Em uma atualização, a MalwareTech diz que a análise do tráfego de rede não indica autopropagação, o que significa que o servidor que está fazendo a exploração obtém os endereços IP de destino de uma lista predefinida.

> [![](https://pbs.twimg.com/profile_images/1191143294786363392/K0jSiD-k_normal.jpg)](https://twitter.com/MalwareTechBlog)
> 
> [
> 
> MalwareTech
> 
> ✔@MalwareTechBlog
> 
> ](https://twitter.com/MalwareTechBlog)
> 
> [Replying to @MalwareTechBlog](https://twitter.com/_/status/1190730471321112577)
> 
> Update: according to netflow it doesn't appear to be self propagating, I assume a list of vulnerable IPs are being fed to a server which performs the exploitation.
> 
> [
> 
> 92](https://twitter.com/intent/like?tweet_id=1190802833324462081 "Like")
> 
> [10:28 PM - Nov 2, 2019](https://twitter.com/MalwareTechBlog/status/1190802833324462081)
> 
> [Twitter Ads info and privacy](https://support.twitter.com/articles/20175256 "Twitter Ads info and privacy")

[

23 people are talking about this

](https://twitter.com/MalwareTechBlog/status/1190802833324462081 "View the conversation on Twitter")

A [primeira exploração pública do BlueKeep](https://www.bleepingcomputer.com/news/security/public-bluekeep-exploit-module-released-by-metasploit/)  foi adicionada ao Metasploit em setembro, mas os [scanners](https://www.bleepingcomputer.com/news/security/finding-windows-systems-affected-by-bluekeep-remote-desktop-bug/) para o bug já estavam disponíveis antes dessa data. A análise da MalwareTech confirmou que o mesmo código no módulo Metasploit também está presente no malware.

![](https://www.bleepstatic.com/images/news/u/1100723/KernelShellcodeCompare-MalwareTech.png)

fonte: [Kryptos Logic](https://www.kryptoslogic.com/blog/2019/11/bluekeep-cve-2019-0708-exploitation-spotted-in-the-wild/)

É provável que quem está por trás desses ataques esteja usando recursos públicos e não tenha desenvolvido uma ameaça confiável e passível de worms, como comprovado pelas falhas de honeypot de Beaumont.

Uma combinação de minerador de criptomoeda e um scanner BlueKeep foi [relatada em julho](https://www.bleepingcomputer.com/news/security/bluekeep-scanner-discovered-in-watchbog-cryptomining-malware/) em um malware chamado Watchbog, que geralmente se concentrava em servidores Linux vulneráveis.

Na época, a empresa de segurança cibernética Intezer disse que a integração do módulo de scanner para a vulnerabilidade RDP juntamente com as explorações do Linux "sugere que o WatchBog está preparando uma lista de sistemas vulneráveis ​​para segmentar no futuro ou vender para fornecedores de terceiros com fins lucrativos".

A MalwareTech nos disse que os indicadores de comprometimento que o Intezer forneceu para o Watchbog não parecem coincidir com o malware atualmente atingindo máquinas vulneráveis ​​ao BlueKeep.

Esses ataques geraram mais de 26 milhões de eventos na infraestrutura de honeypot da Beaumont, o que torna a determinação dos indicadores de comprometimento uma tarefa mais demorada. No entanto, o pesquisador prometeu classificá-los para a sequência relevante e fornecer os dados.

![](https://www.bleepstatic.com/images/news/u/1100723/BlueKeepEvents-Beaumont.jpeg)

fonte: [Kevin Beaumont](https://twitter.com/GossiTheDog/status/1190744823759851521?s=20)

  

Breve história do BlueKeep
--------------------------

O BlueKeep (CVE-2019-0708) é uma vulnerabilidade séria que pode permitir que o malware se espalhe pelos sistemas conectados sem a intervenção do usuário. A Microsoft o corrigiu em 14 de maio, seguida por uma enxurrada de alertas sobre sua gravidade por parte de governos e empresas de segurança, alguns reiterando sua preocupação.

Explorar essa falha do RDP para execução remota de código (RCE) não é fácil e o resultado mais comum desse esforço é uma falha no sistema de destino. Os pesquisadores de segurança que criaram uma exploração em funcionamento [mantiveram os detalhes privados](https://www.bleepingcomputer.com/news/security/bluekeep-remote-desktop-exploits-are-coming-patch-now/)  para atrasar os invasores na criação de sua versão e comprometer os sistemas ainda sem patch.

Dois módulos de exploração privada foram desenvolvidos em junho e julho, [para as](https://www.bleepingcomputer.com/news/security/metasploit-module-created-for-bluekeep-flaw-private-for-now/)  ferramentas de teste de penetração [Metasploit](https://www.bleepingcomputer.com/news/security/metasploit-module-created-for-bluekeep-flaw-private-for-now/)  e [CANVAS](https://www.bleepingcomputer.com/news/security/bluekeep-rce-exploit-module-added-to-penetration-testing-tool/) . Ambos eram difíceis de obter, pois o primeiro era privado e o segundo foi entregue a assinantes que pagavam pelo menos US $ 32.480.

No nível corporativo, a taxa de atualização mundial foi de 83% em junho. No entanto, essa estatística não contava com máquinas de consumo. Isso sugere que os cibercriminosos provavelmente estão atingindo os computadores dos consumidores.

A vulnerabilidade não afeta todas as versões do sistema operacional Windows. O [comunicado](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2019-0708) da Microsoft lista o Windows 7, o Windows Server 2008 R2 e o Windows Server 2008.

Atualização \[03/03/2019\]:  artigo atualizado com informações da [análise do malware](https://www.kryptoslogic.com/blog/2019/11/bluekeep-cve-2019-0708-exploitation-spotted-in-the-wild/) pela MalwareTech no blog Kryptos Logic.