---
title: 'OSINT: contra-inteligência nas guerras corporativas'
date: 2019-12-31T06:59:00+01:00
draft: false
---

Guia OSINT: contra-inteligência nas guerras corporativas
========================================================

[![Lampyre.io](https://miro.medium.com/fit/c/96/96/0*pmBVIJ_9qpF7BItU)](https://medium.com/@lampyre.io?source=post_page-----501255bc27b3----------------------)

[Lampyre.io](https://medium.com/@lampyre.io?source=post_page-----501255bc27b3----------------------)

Segue

[30 de dezembro](https://medium.com/@lampyre.io/osint-guide-counterintelligence-in-corporate-wars-501255bc27b3?source=post_page-----501255bc27b3----------------------) · 5 min de leitura

Hoje, falaremos sobre a aplicação de técnicas OSINT e demonstraremos como realmente são importantes as medidas preventivas nos negócios ao verificar possíveis parceiros.

_Este caso é baseado em uma história verdadeira. Para preservar a confidencialidade, todos os dados pessoais foram alterados para fictícios e não são reais._

![](https://miro.medium.com/max/60/1*_fjyz9pXvnpP5FV06KROAQ.jpeg?q=20)

![](https://miro.medium.com/max/500/1*_fjyz9pXvnpP5FV06KROAQ.jpeg)

Pensemos em uma feira de TI em Los Angeles e imaginemos que você é um expositor lá. Então, no evento, chega um visitante - o Sr. X, ele oferece seu cartão de visita e sugere agendar uma reunião para discutir as peculiaridades técnicas da sua solução. Este cartão de visita também possui o nome da empresa do Sr. X - empresa T e seu número de telefone.

Esse cara parece muito insistente para você, então, pouco antes dessa reunião programada, você decide aprender mais sobre ele e a empresa que ele representa.

Bem, vamos começar!

Você tem um número de telefone no cartão de visita +1234567890.

Agora vamos iniciar o Lampyre e executar todas as solicitações de 'Pesquisar por número'. Em seguida, tentaremos verificar outros dados nesse cartão de visita executando mais algumas solicitações.

![](https://miro.medium.com/max/60/1*01jip0_o_2M6s3GeidkbzA.png?q=20)

![](https://miro.medium.com/max/583/1*01jip0_o_2M6s3GeidkbzA.png)

Este é o nosso resultado:

![](https://miro.medium.com/max/60/1*LX1hw5IDt1vctDxmvSQvQg.png?q=20)

![](https://miro.medium.com/max/702/1*LX1hw5IDt1vctDxmvSQvQg.png)

Após analisar as informações obtidas, indiretamente, podemos confirmar os dados desse cartão de visita. No entanto, sabemos por experiência própria que quaisquer dados podem ser falsos e devemos continuar nossa pesquisa.

Uma das ferramentas certas para verificar quem posta online é estudar o ambiente em redes sociais.

![](https://miro.medium.com/max/60/1*A1qyELRLuSlbyE03-6O3bw.png?q=20)

![](https://miro.medium.com/max/406/1*A1qyELRLuSlbyE03-6O3bw.png)

É por isso que ficamos tão animados quando vimos os resultados de nossa solicitação de pesquisa do Foursquare. O Sr. X - a pessoa que nos preocupa - não se esforçou muito para esconder. Embora não tenhamos encontrado nada diretamente com a solicitação 'conta do Facebook por número de telefone', descobrimos que ele postou um link para o Facebook no perfil do Foursquare e ainda assim conseguimos.

Agora, com esses novos dados, podemos iniciar solicitações de pesquisa diretamente no gráfico:

![](https://miro.medium.com/max/60/1*hym-27LSa0uCchu-skoIug.png?q=20)

![](https://miro.medium.com/max/457/1*hym-27LSa0uCchu-skoIug.png)

Então, enriquecemos nossos dados com os do Facebook e é isso que temos:

![](https://miro.medium.com/max/60/1*K7FwZm4MNkbjYiwOwYBtIA.png?q=20)

![](https://miro.medium.com/max/564/1*K7FwZm4MNkbjYiwOwYBtIA.png)

Existem duas empresas mencionadas no perfil do Facebook, uma delas corresponde à do cartão de visita. Mas estamos avançando e lançando uma solicitação para procurar amigos do Facebook:

![](https://miro.medium.com/max/60/1*UUbJS-8f29DLCnmSz-VCKw.png?q=20)

![](https://miro.medium.com/max/340/1*UUbJS-8f29DLCnmSz-VCKw.png)

As informações que obtemos nos permitem criar um mapa da localização dos amigos do Sr. X. Oh, parece que o Sr. X tem amigos em todo o mundo!

![](https://miro.medium.com/max/60/1*okyzM5j5c_WlvcBnAgOmSw.png?q=20)

![](https://miro.medium.com/max/639/1*okyzM5j5c_WlvcBnAgOmSw.png)

Vamos fazer um gráfico de amigos e ver as estatísticas de onde eles trabalharam:

![](https://miro.medium.com/max/60/1*HukffGR_GJgi4WrGWX1SUQ.png?q=20)

![](https://miro.medium.com/max/513/1*HukffGR_GJgi4WrGWX1SUQ.png)

![](https://miro.medium.com/max/60/1*2VOp89RrFeN7AivSDzPxUw.png?q=20)

![](https://miro.medium.com/max/647/1*2VOp89RrFeN7AivSDzPxUw.png)

Como vemos claramente, não há nenhuma empresa T, mencionada nesse cartão de visita, nas estatísticas. Espere, o que?!… O Sr. X não tem amigos da empresa T? Então, por que ele tem tantos amigos de outras empresas?

Podemos concluir que essa pessoa alterou as informações do perfil para que correspondam aos dados do cartão de visita. Seu ambiente, é claro, permaneceu o mesmo e isso deixa o local real de trabalho.

Além disso, observe que a empresa S é sua concorrente direta. Provavelmente, foi assim que eles planejaram espionar você.

Também vale a pena destacar a solicitação 'Informações de identificação de chamada por número de telefone'. Ele mostra os nomes sob os quais o número de telefone está armazenado nas listas telefônicas de outras pessoas.

Portanto, os dados obtidos confirmam que o Sr. X está definitivamente relacionado à empresa S, pois seu número de telefone está marcado com esse nome na lista telefônica de muitas pessoas.

![](https://miro.medium.com/max/60/1*W93QT5oIO8H-WH4V5AeWeg.png?q=20)

![](https://miro.medium.com/max/702/1*W93QT5oIO8H-WH4V5AeWeg.png)

Bem, devemos ligar para a empresa S e pedir para falar com o Sr. X? ; )

Pesquisando os arredores de seu objeto de interesse, muitas vezes descobrimos muitas coisas peculiares e às vezes inesperadas. E pode não ser apenas descobrir seu verdadeiro empregador! Estudar grupos de usuários, que têm isso ou aquilo em comum, por exemplo, pode apontar para o local real de nascimento (por exemplo, a pessoa mantém contato com seus colegas de escola) ou para o local onde ele teve sua graduação. Tudo isso, por sua vez, inspira seu pensamento analítico e outras pesquisas. Você poderia continuar e continuar, mas com o Sr. X paramos aqui, tendo atingido nosso objetivo.

Oh, as maravilhas deste mundo OSINT !!! :)

_PS Se você tiver alguma sugestão sobre os tópicos de novos artigos ou solicitações de Lampyre, informe-nos!_

_Tenha muitas investigações emocionantes!_