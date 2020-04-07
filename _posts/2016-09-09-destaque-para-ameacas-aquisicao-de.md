---
title: 'Destaque para ameaças: aquisição de conta de e-mail'
date: 2020-02-12T16:36:00+01:00
draft: false
---

Cuidado: os invasores estão encontrando novas maneiras de evitar a detecção quando comprometem as contas de email.  
  
Pesquisadores da Barracuda e da UC Berkeley, realizando uma análise em larga escala da aquisição de contas de email e a linha do tempo dos ataques, destacaram recentemente os comportamentos que os hackers estão usando para tentar evitar a detecção, maneiras de identificar atividades suspeitas que possam indicar que uma conta de email foi comprometida e as precauções que você pode tomar para proteger seus negócios.  
  
Entre as principais conclusões: os  
  
ataques se espalham por um período de tempo; nem sempre acontecem assim que a conta é comprometida  
Os atacantes estão ficando mais espertos sobre a geografia; eles enviam e-mails de phishing e executam outras ações de IPs vinculados a regiões e países semelhantes dos  
endereços IP da conta invadida e os ISPs fornecem dicas importantes; invasores tendem a usar IPs anônimos pertencentes a provedores de serviços de Internet diferentes do provedor da conta invadida  
Aqui está uma visão mais detalhada da aquisição de contas, incluindo uma análise detalhada da linha do tempo e o que ela revela sobre as táticas em evolução dos cibercriminosos, além de práticas recomendadas e soluções para ajudar detectar e bloquear ataques.  
  
Ameaça destacada  
Aquisição de conta de email - Os cibercriminosos usam a representação de marca, engenharia social e phishing para roubar credenciais de login e acessar uma conta de email. Depois que a conta é comprometida, os hackers monitoram e rastreiam as atividades para saber como a empresa faz negócios, as assinaturas de email que usam e a maneira como as transações financeiras são manipuladas, para que possam iniciar ataques de phishing subsequentes, incluindo a coleta de informações financeiras e credenciais de login adicionais para outras contas.  
  
Os hackers executam ataques de controle de contas usando uma variedade de métodos. Em alguns casos, os hackers utilizam nomes de usuário e senhas adquiridos em violações de dados anteriores. Como as pessoas costumam usar a mesma senha para contas diferentes, os hackers podem reutilizar com sucesso as credenciais roubadas e obter acesso a contas adicionais. Os hackers também usam senhas roubadas para emails pessoais e usam acesso a essa conta para tentar obter acesso a emails comerciais. Os ataques de força bruta também são usados ​​para controlar as contas com êxito, porque as pessoas usam senhas muito simples, fáceis de adivinhar, e não as alteram com frequência suficiente. Os ataques também ocorrem por meio de aplicativos da web e de negócios, incluindo SMS.  
  
Para fornecer uma análise detalhada da linha do tempo de um ataque de aquisição de conta, os pesquisadores usaram uma combinação dos detectores de inteligência artificial (AI) do Barracudas para compilar uma lista de usuários cujas contas foram comprometidas em agosto de 2019. Os pesquisadores escolheram uma conta comprometida, conhecida como Usuário X e analisou as propriedades de logon do Microsoft Azure e a atividade de email por volta do momento do primeiro sinal de possível comprometimento. Além dos dados dos detectores do Barracuda, os pesquisadores tiveram acesso aos e-mails não processados, incluindo a linha de assunto, o conteúdo do corpo e o endereço IP de origem, bem como os aplicativos Microsoft utilizados, incluindo o endereço IP, o horário do login e as operações. realizada.  
  
Essa linha do tempo analisa atividades suspeitas na conta do Usuário X durante as três semanas em torno da primeira detecção sinalizada, avaliando três características de cada evento: a data e a hora UTC, o estado e o país de origem da atividade, com base na localização geográfica do endereço IP e a operação realizada.  
  
Identificando o comportamento do invasor  
  
Comparando a atividade de características antes da primeira detecção sinalizada com a atividade nas semanas após a detecção, os pesquisadores descobriram vários indicadores de comportamento do invasor, como logins de IPs pertencentes a cidades e estados diferentes da cidade e estado típico dos quais o usuário efetua login. O usuário X normalmente faz logon em duas cidades do Texas, mas a conta estava sendo usada na Indonésia e em vários lugares nos Estados Unidos, incluindo Arizona, Nova York e Virgínia.  
  
Para confirmar isso como um indicador de logins de invasores, os pesquisadores analisaram e-mails enviados pelo Usuário X durante o período de três semanas a partir da detecção inicial e observaram que e-mails com assuntos semelhantes a phishing eram enviados por IPs fora dos locais típicos em que o usuário X fazia login. . Além disso, os eventos de logon e as atividades de e-mail que provavelmente estavam vinculadas a um invasor quase sempre se originavam de serviços de IP e hospedagem anônimos, como [GoDaddy.com](http://godaddy.com/) e Google Cloud.  
  
Principais conclusões O  
tempo pode ser espalhado  
  
A maior parte deste ataque ao usuário X ocorreu dentro de um período de dois dias, mas houve um intervalo de 12 dias entre o login inicial da Indonésia e outras atividades suspeitas.  
  
Uma hipótese potencial sobre a longa lacuna é que o invasor está tentando realizar um ataque de reconhecimento gastando tempo coletando informações da lista de contatos do Microsoft Outlook do usuário X. Outra possibilidade é que um invasor tenha comprometido a conta do Usuário X e depois vendido as credenciais para outro invasor, causando uma lacuna no comportamento suspeito.  
  
Esse primeiro login é uma pergunta sem resposta em termos do objetivo em potencial. Independentemente de o invasor estar fazendo reconhecimento ou vendendo as credenciais para outro invasor, identificar a aquisição da conta o mais rápido possível e corrigir rapidamente pode ajudar a evitar danos adicionais.  
  
Os invasores estão ficando mais inteligentes sobre geografia  
  
Doze dias após o login inicial da Indonésia, em 7 de agosto, há uma série de três conjuntos diferentes de logins e e-mails enviados de diferentes IPs anônimos originários de Scottsdale, Arizona e em algum lugar de Nova York. Em cada instância, apenas um email é enviado, o que pode ser um sinal de um invasor enviando um único email de teste em preparação para um possível ataque maior.  
  
Dois dias depois, em 9 de agosto, há um longo conjunto de cerca de 50 e-mails de phishing enviados de Scottsdale, Arizona. (Observação: a maioria dos 50 eventos de email foi removida da linha do tempo por concisão.) Depois, há uma série de logons estrangeiros no servidor de email da conta do Usuário X, mas nenhum email foi enviado. Finalmente, há uma série de e-mails de phishing enviados de um IP vinculado a algum lugar da Virgínia.  
  
O fato de a maioria dos e-mails de phishing terem sido enviados de IPs localizados nos Estados Unidos pode indicar que os invasores tentam evitar a detecção executando a maior parte de suas ações de IPs vinculados a regiões / países semelhantes aos verdadeiros usuários. Essa abordagem fará com que a atividade pareça menos anômala do que a atividade proveniente de regiões estrangeiras. Como resultado, sem olhar mais de perto os e-mails enviados de outros locais nos Estados Unidos, teria sido difícil identificar se a atividade de login nesses locais era atribuível aos invasores.  
  
Endereço IP e ISP são pistas importantes  
  
Os invasores tendem a usar IPs anônimos pertencentes a ISPs diferentes do provedor de ISP típico do usuário real. Também havia uma correspondência 1-1 entre o endereço IP de origem dos emails enviados da conta do Usuário X e o endereço IP usado durante o logon no Microsoft Outlook. Isso ajudou a vincular eventos de login e atividades de email a possíveis invasores.  
  
Proteção contra controle de controle de conta de email  
Monitore o acesso à conta e as regras da caixa de entrada  
  
Seja detalhado com seu monitoramento. Use a tecnologia para identificar atividades suspeitas, incluindo logins em horários incomuns do dia ou em locais e endereços IP incomuns, sinais potenciais de uma conta comprometida. Rastreie IPs que exibem outros comportamentos suspeitos, incluindo logins com falha e acesso de dispositivos suspeitos.  
  
Também monitore contas de email para regras maliciosas de caixa de entrada, pois elas costumam ser usadas como parte da aquisição da conta. Os criminosos fazem login na conta, criam regras de encaminhamento e ocultam ou excluem qualquer email que eles enviam da conta, para tentar encobrir seus rastros.  
  
Treine funcionários para reconhecer e relatar ataques  
Eduque os usuários sobre ataques de spear-phishing, fazendo parte do treinamento de conscientização sobre segurança. Garanta que os funcionários reconheçam ataques projetados para roubar credenciais de login e que saibam como denunciar ataques. Use a simulação de phishing para e-mails, correio de voz e SMS para treinar usuários para identificar ataques cibernéticos, testar a eficácia do seu treinamento e avaliar os usuários mais vulneráveis ​​a ataques. Ajude os funcionários a evitar erros dispendiosos criando diretrizes que implementam procedimentos para confirmar solicitações recebidas por email, incluindo transferências eletrônicas e compra de cartões-presente.  
  
Usar autenticação multifator  
A autenticação multifatorial, também denominada MFA, autenticação de dois fatores e verificação em duas etapas, fornece uma camada adicional de segurança acima e além do nome de usuário e senha, como código de autenticação, impressão digital ou digitalização da retina.  
  
Aproveite a inteligência artificial Os  
golpistas estão adaptando táticas de e-mail para ignorar gateways e filtros de spam, por isso é essencial ter uma solução que detecte e proteja contra ataques de spear-phishing, incluindo comprometimento de e-mail comercial e aquisição de conta de e-mail. Implante uma tecnologia criada especificamente para isso, que não depende apenas de procurar links ou anexos maliciosos. O uso do aprendizado de máquina para analisar padrões de comunicação normais em sua organização permite que a solução identifique anomalias que podem indicar um ataque.  
  
Implante proteção contra controle de conta  
Alguns dos ataques de spear-phishing mais devastadores e bem-sucedidos se originam de contas comprometidas. Certifique-se de que os golpistas não estejam usando sua organização como base para lançar esses ataques. Implante a tecnologia que usa inteligência artificial para reconhecer quando as contas foram comprometidas e que corrige em tempo real, alertando os usuários e removendo emails maliciosos enviados de contas comprometidas.

Mais informações:

[https://blog.barracuda.com/2020/02/06/threat-spotlight-email-account-takeover/](https://blog.barracuda.com/2020/02/06/threat-spotlight-email-account-takeover/)