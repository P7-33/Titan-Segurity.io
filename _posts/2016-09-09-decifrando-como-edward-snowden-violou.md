---
title: 'Decifrando como Edward Snowden violou a NSA [cinco anos depois]'
date: 2019-11-30T16:40:00+01:00
draft: false
---

### Exceder o acesso autorizado - um documento de instruções da NSA

Bem, já se passaram cinco anos desde o lançamento do CitizenFour (e mais de um ano desde que Snowden deu seus documentos aos jornalistas, é claro). E, durante todo esse tempo, uma pergunta premente na comunidade de segurança é esta: diante dos melhores esforços do serviço de inteligência digital mais avançado do mundo, como um rapaz conseguiu roubar tanto?  
  
  
Agora, finalmente, com a publicação do livro de Snowden, "Permanent Record \[amazon.com\]", temos sua própria resposta para essa pergunta - e não é ninguém que a comunidade tenha previsto.  
 

**[Você sabe quem está usando as identidades da sua máquina? Leia o nosso Guia de manequins.](https://www.venafi.com/resource/machine-identity-dummies?utm_source=blog&utm_medium=CTA&utm_campaign=Snowden-5-years-later-blog)**  
 

### Preparando o Palco  
  
![](https://www.venafi.com/sites/default/files/content/body/shutterstock_488914813.jpg)

Na ausência de qualquer resposta da própria NSA (e tornou-se rapidamente óbvio que mesmo a NSA não tinha idéia do que ele havia tomado), abundavam as especulações, e a maioria delas se centrou no "manual de instruções" padrão para um privilegiado. Isso faz sentido, é claro; Snowden foi arquiteto e administrador de sistemas NSA específicos (também conhecido como "SysAdmin") e, como tal, tinha autoridade ilimitada nesses sistemas. No entanto, o escopo e o número dos documentos divulgados sugeriam que Snowden tinha acesso muito mais amplo do que seria consistente com essa autoridade. Em particular, ele divulgou documentos não apenas em seu próprio site, mas em outros sites, agências federais aliadas e até mesmo agências de países aliados.  
 

No manual padrão, isso só poderia significar uma coisa: credenciais roubadas. Usando seu acesso aos sistemas que ele controlava, presume-se que ele obtivesse acesso às credenciais dos usuários naqueles sistemas que também tinham acesso a outros, permitindo que ele "passasse" pela rede da NSA para sites que ele normalmente não visitaria, e sistemas que ele normalmente não podia tocar. Ao usar esses bens roubados, ele poderia parecer (para esses outros sistemas) aqueles usuários legítimos e, portanto, não acionava alarmes. Como ele então extraiu e escapou com os dados pareceria então outra pergunta, mas mais uma vez respondeu por sua posição privilegiada.  
 

_NOTA: Os administradores de sistemas geralmente precisam aplicar patches, reparar ou restaurar arquivos de sistema e executar outras tarefas que não podem ser executadas em uma rede; portanto, geralmente têm direitos de usar "mídia removível" que um usuário normal não faria._  
 

A comunidade adotou essa teoria, porque ela se encaixava nos fatos como eram conhecidos e enfatizou as lições que eles estavam lutando para transmitir localmente - que o controle das credenciais era crítico (e que as credenciais não seguras que estão em um servidor também podem estar presentes). à vista); que os logs devem ser monitorados para acesso não característico, mídia removível bloqueada e assim por diante. Era uma lição objetiva e um exercício de humildade. Se mesmo a grande NSA pudesse sofrer uma violação, apesar de práticas inadequadas, isso poderia acontecer com QUALQUER UM.  
 

No entanto, algumas coisas não se encaixavam. A NSA é conhecida por ser observadora de logs obsessiva e levar a análise comportamental a uma arte. Além disso, a NSA acredita firmemente que somente o hardware pode ser confiável; portanto, criou (no início do novo século) uma variação no Linux padrão chamada "Linux com segurança aprimorada". O SELinux reduz o papel do administrador de sistemas do superusuário "root" ilimitado do linux / unix padrão para um conjunto de permissões muito mais variadas que não permitiam desativar o log (ou modificar os logs), alterando certos arquivos principais do sistema e as configurações, e assim por diante. Portanto, qualquer tentativa de acessar credenciais armazenadas por seus usuários deveria ter sido registrada e, na auditoria desses logs, uma explicação precisaria ser apresentada ou ele estaria com muitos problemas. Nesse ambiente, a única maneira de um Snowden acontecer seria se a NSA tivesse adormecido ao volante (e isso é possível; o tempo gasto espionando seu próprio povo é o tempo que você não está espionando "o inimigo"). Isso pode implicar pelo menos que, após o fato, eles saberiam em triplicado exatamente quais arquivos ele acessara, para onde os copiara e onde deveria estar agora.  
 

Mas se isso não aconteceu, o que aconteceu?  
 

  

### O livro do filme  
  
![](https://www.venafi.com/sites/default/files/content/body/shutterstock_1353332507_0.jpg)

Em seu livro, Snowden avança uma sequência completamente diferente de eventos, e a chave dessa narrativa é o papel que ele foi pago para desempenhar na rede da NSA.  
 

Durante uma missão anterior com a agência, Snowden foi encarregado de fazer exatamente o que ele faria mais tarde para seus próprios propósitos - verificar vários sites da NSA em busca de arquivos confidenciais, copiar esses arquivos para um servidor remoto e examiná-los. No processo, ele não apenas determinava a classificação de segurança de arquivos confidenciais (e, portanto, quem poderia acessar essas cópias de backup), mas localizava e "mesclava" cópias duplicadas do mesmo documento em um processo que os engenheiros de backup chamam de "instância única" ou " desduplicação ". Há pouco mérito em ter trezentas cópias de backup do mesmo documento, apenas porque trezentos agentes possuíam sua própria cópia pessoal. Este projeto foi chamado EPICSHELTER e seu objetivo era fornecer resiliência diante de perdas catastróficas; se (digamos) uma base de satélites da NSA foi destruída; cópias de backup de seus documentos existiriam no sistema e poderiam ser alocadas a outros agentes. Este sistema não era DIRETAMENTE um fator, mas seria um sistema relacionado posterior.  
 

A próxima função de Snowden seria o único funcionário do "Escritório de compartilhamento de informações" - onde ele se descreve como um "Administrador do SharePoint", encarregado de manter um sistema de gerenciamento de documentos para o site do Havaí. Isso foi resumido em uma página de visão geral chamada "painel de leitura", que é basicamente um feed de notícias para atualizações de status classificadas - permitindo que os usuários do site vejam a imagem maior e identifiquem se o trabalho de algum outro funcionário se sobrepunha ao seu.  
 

Snowden estava lendo, não apenas a tabela de leitura de seu próprio site, mas também dos sites em que ele estava anteriormente - isso é rotina para qualquer nerd com um sistema de gerenciamento de conteúdo. Ele logo automatizou isso, puxando as placas de leitura para vários sites em seu sistema SharePoint e exibindo-a como uma "meta-leitura". À medida que crescia, Snowden buscou (e obteve) a aprovação oficial para expandir o sistema, não apenas puxando cada vez mais dados, mas compartilhando-o com outros funcionários da NSA, para que eles só pudessem ver entradas em seu próprio nível de liberação ou inferior. À medida que o novo sistema "Heartbeat" crescia, ele se expandia para extrair dados não apenas de outros sites da NSA, mas da CIA, do FBI e até do Sistema Conjunto Mundial de Comunicações Inteligentes, com a cooperação ativa dos administradores de documentos desses sites.  
 

  

### O elo perdido

![](https://www.venafi.com/sites/default/files/content/body/shutterstock_682753654%20(1).jpg)

Aqui, pelo menos, está o link que faltava; Snowden não precisava de credenciais adicionais (o que também é bom). Em seu livro, Snowden detalha que as credenciais são certificados PKI e chaves armazenadas em tokens físicos, que funcionam como emblemas de identidade. Esses tokens literalmente não podem ser roubados sem destruir os emblemas no processo. Mas ele precisava levar os arquivos sem trégua de "Heartbeat" para a mídia que levou para Hong Kong (que é claro que ele também cobre em seu livro).  
 

Então, olhando para isso, vemos uma história muito mais sutil, mas com menos saltos de fé. Ao criar e expandir esse sistema, Snowden (com total aprovação de sua gerência) se colocou em uma posição sem precedentes - capaz de manipular o código que controla o acesso a vastas faixas de informações de inteligência. Depois que ele decidiu abusar dessa confiança, o resultado parece inevitável, mas, na verdade, essa é uma consequência natural do risco interno que os principais insiders representam. Mesmo para a NSA, haverá indivíduos que podem tornar-se desonestos, e eles podem não ser diretores ou mesmo gerentes, mas alguns nerds em um escritório remoto que você nunca ouviu falar ... até que todos tenham ouvido falar deles.  
 

**As identidades da sua máquina estão protegidas contra ameaças internas?**

  

Descubra por que a Proteção de identidade de máquina é relevante no atual clima de alto risco de segurança cibernética. 

  

  

  

**Se você está interessado em história, veja como Venafi estimou que os eventos podem ter acontecido há 5 anos.**  
 

Até o momento, poucas informações reais existem publicamente para explicar como Edward Snowden roubou segredos de uma das organizações de inteligência mais avançadas e sofisticadas do mundo. Relatórios sobre "Como Snowden fez isso" detalham pouco mais do que o óbvio: ele violou a Agência de Segurança Nacional (NSA). Como especialistas em garantir e proteger a confiança estabelecida por chaves e certificados, Venafi entende como Snowden realizou essa violação. Para desenvolver esse entendimento, os analistas de segurança da Venafi analisaram metodicamente as informações públicas por mais de 3 meses, conectaram peças do quebra-cabeça com base em nosso conhecimento de ataques e vulnerabilidades no Global 2000 e solicitaram a revisão por pares e feedback de especialistas do setor.  
 

Ironicamente, a planta e os métodos para o ataque de Snowden eram bem conhecidos pela NSA. A NSA não precisou procurar além do ataque Stuxnet dos EUA para entender sua vulnerabilidade. Claramente, Edward Snowden entendeu isso. Aqui, descrevemos como Venafi resolveu esse quebra-cabeça e explicamos por que as ações de Snowden afetam não apenas a NSA, mas sua organização.  
 

Se estivermos errados, convidamos a NSA e Edward Snowden a nos corrigir. O diretor geral da NSA, Keith Alexander,  [quer promover o compartilhamento de informações](http://threatpost.com/nsas-alexander-appeals-for-threat-information-sharing/102404) e agora é a oportunidade perfeita. O general Alexander  [declarou:](http://www.businessinsider.com/nsa-firing-sysdadmins-2013-8)  "No final das contas, trata-se de pessoas e confiança" e concordamos. Os ataques de confiança que violaram a NSA são vulnerabilidades em todas as empresas e governos. Compartilhar como a violação foi pesquisada e executada é importante para ajudar todas as empresas a proteger sua valiosa propriedade intelectual, dados de clientes e reputação. Acreditamos que a NSA e Edward Snowden concordariam que ajudar empresas e governos a melhorar sua segurança é uma causa digna.  
 

##### Informações limitadas (leia-as como não) até o momento foram compartilhadas publicamente

Nem os  [relatórios de investigação](http://investigations.nbcnews.com/_news/2013/08/26/20197183-how-snowden-did-it)  nem as  [declarações públicas](http://rt.com/usa/nsa-snowden-lonny-anderson-038/)  da liderança da NSA explicaram os métodos que Snowden usou para violar a segurança da NSA.

Aqui está o que sabemos sobre o ambiente de trabalho de Snowden e as ferramentas que ele tinha à sua disposição:  
 

1.  Acesso válido - Como contratado, a Snowden recebeu um Cartão de Acesso Comum (CAC) válido. Esse cartão inteligente pré-carregou chaves criptográficas e certificados digitais que autenticavam sua identidade e forneciam status básico confiável e acesso às informações e sistemas aos quais ele estava autorizado a acessar.  
     
2.  Chaves SSH - Como administrador de sistemas, Snowden usou   chaves [Secure Shell (SSH)](http://en.wikipedia.org/wiki/Secure_Shell) para autenticar e gerenciar sistemas como parte de seu trabalho diário. Antes de trabalhar para a NSA, sabe-se que Snowden  [testou os limites](http://www.nytimes.com/2013/10/11/us/cia-warning-on-snowden-in-09-said-to-slip-through-the-cracks.html?_r=1&)  de seus privilégios de administrador para obter acesso não autorizado a informações classificadas enquanto estava no posto da CIA em Genebra, na Suíça.  
     
3.  Recursos de computação limitados - como muitos invasores externos, Snowden não tinha um compartimento de servidores, computadores Macintosh de ponta ou mesmo um laptop Windows pendurado na rede NSA, conhecida como NSAnet. Foi relatado que Snowden tinha acesso  [básico de terminal ou thin client](http://investigations.nbcnews.com/_news/2013/08/26/20197183-how-snowden-did-it)  ao NSAnet. Ele tinha a mesma visão que um invasor poderia ter depois de uma bem-sucedida missão inicial de intrusão ou reconhecimento.  
     

![](https://www.venafi.com/sites/default/files/content/body/shutterstock_305046326.jpg)

#####   
Montando o quebra-cabeça de como Snowden atacou a confiança para violar a NSA

Depois de entender as ferramentas e o ambiente de rede da Snowden, analisamos as informações que foram relatadas sobre a Snowden e identificamos os elementos críticos que nos ajudariam a reunir a história completa de como a Snowden atacou a confiança estabelecida por chaves criptográficas e certificados digitais para violar a NSA :  
 

*   Snowden fabricou chaves digitais - Em testemunho ao Comitê Permanente de Inteligência da Câmara, o general Alexander explicou que  [Snowden "fabricou chaves digitais" para permitir seu ataque](http://www.businessinsider.com/edward-snowden-copied-a-lot-of-nsa-files-2013-6) . “Fabricando chaves” pode descrever a criação de seus próprios certificados digitais ou outros tipos de chaves criptográficas, como as usadas para acesso SSH.  
     
*   O papel das chaves e dos certificados - No mesmo testemunho do Comitê Permanente de Inteligência da Câmara, a congressista Terri Sewell pediu ao general Alexander que descrevesse o papel e o uso dos certificados digitais na NSA. Como essa linha de questionamento segue o briefing classificado apresentado por Alexander, é altamente provável que o uso de certificados tenha sido discutido no briefing classificado. No contexto de "fabricação" de certificados, certificados autoassinados são criados e emitidos pelo fabricante. Certificados autoassinados são parte comum do kit de ferramentas de criminosos cibernéticos para permitir a exfiltração de dados.  
     
*   Ramificação - Snowden supostamente  [obteve nomes de usuário e senhas](http://www.reuters.com/article/2013/11/08/net-us-usa-security-snowden-idUSBRE9A703020131108)  de dezenas de colegas. Isso deu a ele a oportunidade de estender significativamente seu alcance e tempo para coletar dados. Ao fazer login com as credenciais de seus colegas, ele também teria acesso às chaves SSH e aos certificados digitais. E ele também pode pegar as chaves SSH "fabricadas" e estabelecê-las como confiáveis. Em todos os casos, e diferentemente das senhas que frequentemente precisam ser alteradas, as chaves SSH e os certificados digitais têm uma vida muito mais longa.  
     
*   Segurança perfeita de Snowden - Finalmente, Snowden se gabou de que a criptografia fornece o sistema de segurança perfeito. Em uma [sessão on ](http://www.theguardian.com/world/2013/jun/17/edward-snowden-nsa-files-whistleblower) -  [line de perguntas e respostas com o](http://www.theguardian.com/world/2013/jun/17/edward-snowden-nsa-files-whistleblower)[_The Guardian_](http://www.theguardian.com/world/2013/jun/17/edward-snowden-nsa-files-whistleblower) , Snowden explicou: “A criptografia funciona. Sistemas criptográficos fortes implementados adequadamente são uma das poucas coisas em que você pode confiar. ”Snowden também afirma ter criptografado seus dados roubados para distribuição. Portanto, seu uso de criptografia, que é ativado por chaves SSH e certificados autoassinados, é muito mais provável e suporta a declaração do General Alexander de que Snowden fabricou chaves. [Cisco](http://tools.cisco.com/security/center/viewAlert.x?alertId=28441) ,  [Mandiant](https://www.mandiant.com/blog/md5-sha1/), e outros especialistas há muito tempo estabelecem o uso de sessões criptografadas e autenticadas como uma ferramenta cibercriminosa comum para exfiltrar não detectadas. De fato, já há dez anos, Snowden  [estava perguntando nos fóruns sobre métodos](http://arstechnica.com/tech-policy/2013/06/nsa-leaker-ed-snowdens-life-on-ars-technica/)  para criar conexões anônimas e ofuscadas, e até mencionou o SSH como um método comum.

  

O general Alexander  [resumiu](http://abcnews.go.com/blogs/politics/2013/06/nsa-chief-keith-alexander-system-did-not-work-as-it-should-have-to-prevent-snowden-document-leaks/)  bem a capacidade de Snowden de atacar: “Snowden traiu a confiança que tínhamos nele. Este era um indivíduo com autorização ultra-secreta, cujo dever era administrar essas redes. Ele traiu essa confiança e roubou alguns de nossos segredos. ”Infelizmente, parece que, com tantas organizações com as quais Venafi já trabalhou, a NSA não tinha consciência e capacidade de responder a esses ataques a chaves e certificados.

##### Três etapas importantes na cadeia de mortes

Usando a análise militar de Kill Chain, que  [Lockheed Martin](http://www.lockheedmartin.com/us/what-we-do/information-technology/cyber-security/cyber-kill-chain.html)  e outros tornaram popular em segurança de TI, podemos revelar como Snowden executou seu roubo de dados da NSA:

  

1.  [Pesquisando o alvo -](https://www.venafi.com/blog/post/edward-snowden-breaching-the-nsa-infographic/) Snowden usou seu acesso válido (como CAC com chaves e certificados e chaves SSH para administração do sistema) para determinar quais informações estavam disponíveis e onde foram armazenadas - mesmo que ele não tivesse acesso total a essas informações imediatamente.  
     
2.  [Intrusão inicial -](https://www.venafi.com/blog/post/edward-snowden-breaching-the-nsa-infographic/) Snowden obteve acesso não autorizado a outras chaves SSH administrativas e inseriu o seu para obter status completo e confiável de informações às quais não estava autorizado a acessar. O uso de nomes de usuário e senhas de colegas poderia oferecer a ele mais oportunidades de pegar chaves ou inserir as próprias como confiáveis. Ter um status administrativo “raiz” ou equivalente deu ao Snowden acesso total a todos os dados. Assim como um invasor avançado e persistente, ele tomou o cuidado de [não acionar alarmes e encobrir seus rastros](http://www.nydailynews.com/news/national/u-s-difficulty-uncovering-snowden-trail-article-1.1436093) .  
     
3.  [Exfiltração](https://www.venafi.com/blog/post/edward-snowden-breaching-the-nsa-infographic/) - Para obter os dados do NSAnet, ele não podia simplesmente salvá-los em uma unidade flash. Em vez disso, os dados precisavam ser movidos pelas redes e sob o radar para evitar a detecção. Assim como os cibercriminosos comuns, Snowden usou os servidores de Comando e Controle para receber sessões de dados criptografados. Essas sessões foram autenticadas com certificados autoassinados.

#####   
  
Tudo já foi visto na natureza

Você pode pensar que apenas as equipes cibernéticas avançadas da NSA têm o conhecimento e a habilidade para fabricar certificados autoassinados ou usar chaves SSH não autorizadas para filtrar dados. No entanto, todos esses ataques foram relatados publicamente na natureza. Os cibercriminosos os usaram para lançar ataques bem-sucedidos e continuarão a usá-los. De fato, Snowden seguia, de várias maneiras, os métodos e significa que a NSA já havia usado com sucesso.

  

Em uma das primeiras e mais poderosas demonstrações do que atacar a confiança estabelecida por chaves e certificados pode alcançar, a NSA teria ajudado a realizar os ataques Stuxnet às instalações nucleares iranianas.  [Usando certificados digitais roubados](http://www.economist.com/node/17147818)  de empresas taiwanesas desconhecidas, os arquitetos do Stuxnet,  [identificados por Snowden](http://www.cbsnews.com/8301-205_162-57592862/nsa-leaker-snowden-claimed-u.s-and-israel-co-wrote-stuxnet-virus/)  para incluir a NSA, conseguiram iniciar os ataques do Stuxnet com status confiável. Esses e outros ataques forneceram à Snowden um plano para o ataque: comprometer a confiança estabelecida por chaves e certificados digitais.

  

Mais especificamente para a violação da NSA, os atacantes usaram  [Trojans que roubam chaves SSH](http://www.theregister.co.uk/2012/11/20/freebsd_breach/)  para obter acesso não autorizado a chaves SSH e têm acesso irrestrito ao código fonte do FreeBSD por mais de um mês. Como administrador do sistema, Snowden não precisava usar cavalos de Troia para roubar ou criar suas próprias chaves SSH.

  

Mandiant  [relatou que os atacantes do APT1 geraram certificados autoassinados](http://intelreport.mandiant.com/)  para permitir que seus servidores de comando e controle recebessem dados roubados ocultos e criptografados. Esses certificados não foram completamente detectados como desonestos - pretendendo ser da IBM ou do Google ou para serem usados ​​com "servidor da web" ou "servidor alfa". Ferramentas disponíveis gratuitamente, como o OpenSSL, permitiriam ao Snowden criar certificados autoassinados sob demanda.

  

A lacuna que permitiu que criminosos cibernéticos violem essas e outras organizações é o motivo pelo qual a Forrester Consulting descreveu a situação em termos simples e diretos:  ["Basicamente, a empresa é um pato sentado".](https://www.venafi.com/offers/forrester-attacks-on-trust-webinar/?cid=70150000000o3Ch&utm_source=venafi&utm_medium=blog&utm_content=onsite_link&utm_campaign=snowden)

##### Toda empresa é uma violação da NSA esperando para acontecer

##### Assim como a NSA, a maioria das empresas tem pouca ou nenhuma consciência das chaves e certificados usados ​​para criar confiança - a autenticação, a integridade e a privacidade nas quais quase toda a segurança de TI é construída. De fato, o Instituto Ponemon pesquisou 2.300 grandes organizações e relatou que essas organizações têm, em média, mais de 17.000 chaves e certificados somente em sua infraestrutura principal. Esse número não inclui aplicativos móveis ou as chaves SSH que os administradores usam para acessar sistemas. Ponemon também informou que  [51% das organizações](https://www.venafi.com/offers/ponemon-institute-first-annual-cost-of-failed-trust-report/?cid=70150000000o5Mg&utm_source=venafi&utm_medium=onsite&utm_content=blog_link&utm_campaign=snowden)  não sabem onde e como essas chaves e certificados são usados. E especialistas do setor concordam que esse número é subnotificado.

Todos esses fatos foram claramente aplicados à NSA antes de Snowden violar a segurança da agência e roubar dados. A NSA não tinha conhecimento das chaves e certificados em uso, capacidade de detectar anomalias e capacidade de responder a um ataque. Devido a essas deficiências, o general Alexander  [acredita](http://www.reuters.com/article/2013/08/09/us-usa-security-nsa-leaks-idUSBRE97801020130809)  firmemente que a NSA deve usar inteligência automatizada de máquina para melhorar sua capacidade de detectar e responder a ameaças:

  

“O que estamos fazendo - não é rápido o suficiente - está reduzindo nossos administradores de sistema em cerca de 90%. O que fizemos foi colocar as pessoas no ciclo de transferência de dados, segurança de redes e ações que as máquinas provavelmente são melhores. ”

  

A NSA já está seguindo o caminho que o Gartner  [espera que a maioria das organizações alcance](http://www.gartner.com/id=2500416)  até 2020 ou mais cedo: realocando gastos para focar na detecção e correção de problemas de segurança usando sistemas de segurança rápidos e automatizados. Essa tendência criará uma mudança tectônica na segurança de TI, colocando quase dois terços do orçamento da segurança em detecção e correção, acima dos menos de 10% hoje.

  

Mas o jogo não terminará se esses esforços de detecção e correção não incluírem a segurança e a proteção das chaves e certificados que fornecem a base da confiança no mundo moderno. Portanto, seria aconselhável à NSA seguir  [o conselho da Forrester Consulting](https://www.venafi.com/offers/forrester-attacks-on-trust-webinar/?cid=70150000000o3Ch&utm_source=venafi&utm_medium=blog&utm_content=onsite_link&utm_campaign=snowden) :

“A detecção avançada de ameaças fornece uma camada importante de proteção, mas não substitui a proteção de chaves e certificados que podem fornecer um status confiável ao invasor que evita a detecção.” É claro que Edward Snowden sabia disso. Infelizmente, a NSA não.