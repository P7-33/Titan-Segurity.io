---
title: 'Novo ataque permite que aplicativos Android capturem dados de
alto-falante sem permissão'
date: 2019-09-26T03:20:00+01:00
draft: false
---

[![ataque do canal lateral android ](https://1.bp.blogspot.com/-bc9yZABQubg/XS75xf0CB2I/AAAAAAAA0eU/nDfzBSGXRqgkHtuLEvAwqGgdxIqj-XrDACLcBGAs/s728-e100/android-side-channel-attack.png "ataque do canal lateral android ")](https://1.bp.blogspot.com/-bc9yZABQubg/XS75xf0CB2I/AAAAAAAA0eU/nDfzBSGXRqgkHtuLEvAwqGgdxIqj-XrDACLcBGAs/s728-e100/android-side-channel-attack.png)

No início deste mês, o The Hacker News cobriu uma história de pesquisa que revelou como [mais de 1300 aplicativos Android](https://thehackernews.com/2019/07/android-permission-bypass.html) estão coletando dados confidenciais, mesmo quando os usuários negam explicitamente as permissões necessárias.   
  
A pesquisa foi focada principalmente em como os desenvolvedores de aplicativos abusam de várias maneiras para coletar dados de localização, identificadores de telefone e endereços MAC de seus usuários, explorando os canais secretos e laterais.   
  
Agora, uma equipe separada de pesquisadores de segurança cibernética demonstrou com sucesso um novo ataque de canal lateral que pode permitir que aplicativos mal-intencionados escutem a voz que sai dos alto-falantes do smartphone sem a necessidade de permissão do dispositivo.  
  

Abusando do acelerômetro Android para capturar dados de alto-falantes
---------------------------------------------------------------------

  
[

](https://www.blogger.com/null)Apelidado de **Spearphone** , o ataque recentemente demonstrado tira proveito de um sensor de movimento baseado em hardware, chamado acelerômetro, que é incorporado na maioria dos dispositivos Android e pode ser acessado sem restrições por qualquer aplicativo instalado em um dispositivo, mesmo sem permissões.  

  
Um acelerômetro é um sensor de movimento que permite que os aplicativos monitorem o movimento de um dispositivo, como inclinação, trepidação, rotação ou giro, medindo a taxa de mudança de velocidade no tempo em relação à magnitude ou direção.  

[![reverberações de fala do acelerômetro android](https://1.bp.blogspot.com/-v7ro5gJQxGM/XS764-UHbpI/AAAAAAAA0ek/blX8zgb8fQ83g03q338-QpG485aurjMQQCLcBGAs/s728-e100/android-accelerometer-speech-reverberations.png "reverberações de fala do acelerômetro android")](https://1.bp.blogspot.com/-v7ro5gJQxGM/XS764-UHbpI/AAAAAAAA0ek/blX8zgb8fQ83g03q338-QpG485aurjMQQCLcBGAs/s728-e100/android-accelerometer-speech-reverberations.png)

Como o alto-falante embutido de um smartphone é colocado na mesma superfície que os sensores de movimento incorporados, ele produz reverberações de fala aéreas e de superfície no corpo do smartphone quando o modo de alto-falante está ativado.   
  
Descoberto por uma equipe de pesquisadores de segurança - Abhishek Anand, Chen Wang, Jian Liu, Nitesh Saxena e Yingying Chen - o ataque pode ser desencadeado quando a vítima coloca uma chamada de telefone ou vídeo no modo alto-falante ou tenta ouvir uma mídia arquivo ou interage com o assistente do smartphone.   
  
Como prova de conceito, os pesquisadores criaram um aplicativo Android, que imita o comportamento de um invasor mal-intencionado, projetado para gravar reverberações de fala usando o acelerômetro e enviar os dados capturados de volta para um servidor controlado pelo invasor.  

  
Os pesquisadores dizem que o atacante remoto pode então examinar as leituras capturadas, de maneira offline, usando o processamento de sinais junto com técnicas de aprendizado de máquina "prontas para uso" para reconstruir palavras faladas e extrair informações relevantes sobre a vítima pretendida.  
  

Spearphone Attack: Spy On Calls, anotações de voz e multimídia
--------------------------------------------------------------

  
Segundo os pesquisadores, o ataque do Spearphone pode ser usado para aprender sobre o conteúdo do áudio reproduzido pela vítima - selecionado na galeria de dispositivos na Internet ou notas de voz recebidas nos aplicativos de mensagens instantâneas como o WhatsApp.  
  

> "O ataque proposto pode espionar as chamadas de voz para comprometer a privacidade da fala de um usuário final remoto na chamada", explicam os pesquisadores.   
>   
> "As informações pessoais, como número da previdência social, data de nascimento, idade, detalhes do cartão de crédito, detalhes da conta bancária, etc. consistem principalmente em dígitos numéricos. Portanto, acreditamos que a limitação do tamanho do conjunto de dados não deve subestimar o nível de ameaça percebido pelo nosso ataque. . "

  
Os pesquisadores também testaram seu ataque contra os assistentes de voz inteligentes do telefone, incluindo o Google Assistant e o Samsung Bixby, e capturaram com sucesso a resposta (resultados de saída) a uma consulta do usuário pelo alto-falante do telefone.  

[![falante android hacking](https://1.bp.blogspot.com/-SpnTkU5mFXM/XS76IrmA4EI/AAAAAAAA0ec/E_suRXLr5aAgceBYgBrgw9DU5OmUucBswCLcBGAs/s728-e100/android-speaker-hacking.png "falante android hacking")](https://1.bp.blogspot.com/-SpnTkU5mFXM/XS76IrmA4EI/AAAAAAAA0ec/E_suRXLr5aAgceBYgBrgw9DU5OmUucBswCLcBGAs/s728-e100/android-speaker-hacking.png)

Os pesquisadores acreditam que, usando técnicas e ferramentas conhecidas, o ataque do Spearphone tem "um valor significativo, pois pode ser criado por atacantes de baixo perfil".   
  
Além disso, o ataque Spearphone também pode ser usado para determinar simplesmente algumas características de fala de outros usuários, incluindo classificação de gênero, com mais de 90% de precisão, e identificação de alto-falante, com mais de 80% de precisão.  
  

>  "Por exemplo, um invasor pode saber se um indivíduo em particular (uma pessoa de interesse sob vigilância da polícia) estava em contato com o proprietário do telefone em um determinado momento", dizem os pesquisadores.

  
[Nitesh Saxena](https://twitter.com/saxenaUAB) também confirmou ao The Hacker News que o ataque não pode ser usado para capturar a voz dos usuários-alvo ou seus arredores, porque "isso não é forte o suficiente para afetar os sensores de movimento do telefone, especialmente devido às baixas taxas de amostragem impostas pelo sistema operacional", e portanto, também não interfere nas leituras do acelerômetro.   
  
Para mais detalhes, incentivamos nossos leitores a seguir para o [trabalho completo de pesquisa](https://arxiv.org/pdf/1907.05972.pdf) \[PDF\], intitulado "Spearphone: uma exploração da privacidade da fala por meio de reverberações detectadas por acelerômetro de alto-falantes de smartphones".  
  
O documento também discutiu algumas técnicas de mitigação possíveis que podem ajudar a impedir esses ataques, além de algumas limitações, incluindo baixa taxa de amostragem e variação no volume máximo e na qualidade de voz de diferentes telefones, que podem afetar negativamente as leituras do acelerômetro.   
  
Em um relatório anterior, também explicamos como os aplicativos de malware foram encontrados usando sensores de movimento de dispositivos Android infectados para [evitar a detecção, monitorando](https://thehackernews.com/2019/01/android-malware-play-store.html) se o dispositivo está sendo executado em um emulador de execução ou se pertence a um usuário legítimo com movimentos.

  

Tem algo a dizer sobre este artigo? Comente abaixo ou compartilhe conosco no [Facebook](https://www.facebook.com/thehackernews) , [Twitter](https://twitter.com/thehackersnews) ou em nosso [Grupo do LinkedIn](https://www.linkedin.com/company/the-hacker-news/) .

  
**Fonte: **[feedproxy.google.com](https://feedproxy.google.com/~r/TheHackersNews/~3/RqA6x7PoJpA/android-side-channel-attacks.html)