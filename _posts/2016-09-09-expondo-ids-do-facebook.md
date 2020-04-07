---
title: 'Expondo IDs do Facebook'
date: 2020-02-03T12:11:00+01:00
draft: false
---

Expondo IDs do Facebook
=======================

Mesmo após as alterações na pesquisa de gráficos, o Facebook continua sendo um dos primeiros lugares que as pessoas verificam ao pesquisar uma pessoa ou empresa. Portanto, você geralmente verá muitos links do Facebook em relatórios doxes ou OSINT. O que a maioria das pessoas não sabe é que alguns desses links realmente contêm o ID da conta exclusiva da pessoa que conduz a pesquisa.

Se você acessar o perfil do Facebook de alguém e clicar em qualquer uma das guias como 'Sobre', 'Amigos', 'Fotos' ou qualquer outra, verá que o URL muda para incluir ' ? Lst = ' e três conjuntos de números. Cada número é separado por dois pontos codificados em URL, exibidos como ' % 3A '. Abaixo está um exemplo de como deve ser.

![](https://miro.medium.com/max/60/1*-7VV6te9xZLhWrqqBP5OJg.png?q=20)

![](https://miro.medium.com/max/1402/1*-7VV6te9xZLhWrqqBP5OJg.png)

Exemplo de URL do Facebook contendo IDs

Os detalhes dos números são os seguintes:

*   O número mostrado na caixa verde é o ID do “invasor” ou a conta que está procurando a pessoa.
*   O número na caixa laranja é o ID da "vítima" ou da pessoa que foi pesquisada.
*   O número em vermelho é um carimbo de data / hora do UNIX para mostrar a hora exata em que a pessoa acessou a página.

Portanto, se você visse esse link dentro de um dox, por exemplo, imediatamente diria que a vítima é Chris Hughes , com 5 anos no Facebook , o atacante é 4, o que leva a Mark Zuckerberg , e ele acessou esta página exatamente 10 / 22/2019 às 01:09 (UTC), que você conhece ao converter o carimbo de data / hora usando um site como ' ["); text-decoration-line: none;" target="\_blank">unixtimestamp.com](http://unixtimestamp.com/) '.

Esta não é uma maneira garantida de descobrir quem postou seu perfil, porque muitas pessoas participarão com os números e deixarão seu nome de usuário direcionado ao seu perfil. Além disso, isso mostra a importância do motivo pelo qual todos precisamos de contas fantásticas para que, se você cometeu esse erro em uma investigação real, especialmente uma aplicação da lei em que um link de alguma forma saia, ele não retorne à sua identidade real.

Isso é sempre algo a ser observado se você descobrir que suas próprias informações foram vazadas ou se estiver procurando algo para um cliente. No entanto, na minha experiência, isso não é tão comum de encontrar, porque, como mencionei, a maioria das pessoas postará os links sem os números. Portanto, o que podemos fazer por enquanto é apenas procurar quem postou esses tipos de links na internet.

![](https://miro.medium.com/max/60/1*v3VF8R6u-jJBMFv18n20Fg.png?q=20)

![](https://miro.medium.com/max/656/1*v3VF8R6u-jJBMFv18n20Fg.png)

Pesquisa do Google para doxes com URLs de ID

Fazer a pesquisa do Google acima retorna cerca de 8000 resultados de sites como Pastebin, Doxbin e mais. Isso especifica que eu quero que os resultados incluam ' facebook.com ' e ' ? Lst = ' para encontrar os tipos de URL que desejamos, e também procurará a palavra-chave ' dox ' porque eu queria encontrar pessoas que estavam vazando informação pessoal. Por fim, eu queria excluir quaisquer resultados diretamente do próprio Facebook, porque eu só queria ver os links publicados em outros sites.

![](https://miro.medium.com/max/60/1*UVJrCzxQT9TUSgskGTjuCg.png?q=20)

![](https://miro.medium.com/max/656/1*UVJrCzxQT9TUSgskGTjuCg.png)

Pesquise no Google quaisquer resultados com URLs de ID

A consulta acima é exatamente a mesma que a anterior, mas retirei a palavra-chave ' dox '. Agora, ele diz que existem quase 2,7 milhões de resultados, porque as pessoas normais também postam esses links em todos os lugares, desde perfis do Spotify até repositórios do GitHub. O que mostrarei é um exemplo de um dox em que o doxer vazou suas próprias informações sem saber.

Abaixo está parte de um dox padrão, eu esbatei os detalhes, mas como você pode ver, alguém postou todas as informações pessoais de alguém em Pastebin. Alguns doxes terão uma parte de créditos onde publicarão seu próprio Twitter ou nome de usuário, mas esse não foi o caso com este exemplo. Para o atacante, ele pensou que não havia nada aqui ligando de volta à sua identidade.

![](https://miro.medium.com/max/60/1*9LCBvrBS7mS6YuYovxn0Ag.png?q=20)

![](https://miro.medium.com/max/352/1*9LCBvrBS7mS6YuYovxn0Ag.png)

Exemplo Real Dox

Ao fazer CTRL + F para pesquisar ' lst ' na página, descobri que ele tinha um dos links do Facebook que continha seu próprio ID. O link que ele postou foi para o perfil do pai das vítimas no Facebook.

![](https://miro.medium.com/max/60/1*Te-D4Ti_f44UgmgBkxKGsw.png?q=20)

![](https://miro.medium.com/max/842/1*Te-D4Ti_f44UgmgBkxKGsw.png)

URL de ID no Dox

Você pode acessar o perfil dele digitando 'facebook.com/\[id\]'. Abaixo está o perfil do doxer deste exemplo. Embora algumas vezes você encontre pessoas que usavam contas de bonecos de meias, essa pessoa claramente não o fez. Ele tem muitas fotos de si mesmo, diz onde ele mora e onde estuda, lista sua família e muito mais.

![](https://miro.medium.com/max/60/1*E0ppNJTdgQOKEcykaJ6Ykg.png?q=20)

![](https://miro.medium.com/max/848/1*E0ppNJTdgQOKEcykaJ6Ykg.png)

Perfil de Doxer no Facebook

Como mencionei, isso não se restringe apenas a sites ou cenários específicos. Vimos isso no Pastebin em um dox, mas abaixo está um exemplo de quando esses links foram postados no 4chan. A ideia do 4chan é que as pessoas possam postar enquanto permanecem anônimas, mas para algumas dessas pessoas, esse não é o caso. Além disso, apenas porque o Google retorna apenas 2 resultados para isso, não significa que outros mecanismos de pesquisa ou arquivos não mostrem mais, eles certamente poderiam.

![](https://miro.medium.com/max/60/1*E7vHyxGL64Ur7lfMv2jEuA.png?q=20)

![](https://miro.medium.com/max/649/1*E7vHyxGL64Ur7lfMv2jEuA.png)

URLs de ID encontrados no arquivo 4chan

* * *

Conclusão
=========

As possibilidades são verdadeiramente infinitas com isso. Encontrei algumas dessas URLs em sites do governo que levam você a perfis de pessoas que supostamente trabalham para elas, tenho certeza que o mesmo terá acontecido com policiais e muitos outros. Estou realmente ansioso para ver o que as outras pessoas criam usando isso.

Agora você também tem outro identificador para começar a pesquisar nos mecanismos de pesquisa. Sei que nem sempre procuro IDs do Facebook porque geralmente os associo ao Facebook, mas agora sabemos que você pode encontrá-los em postagens, fóruns e outros sites em Pastebin. Isso poderia ajudar a rastrear uma pessoa para várias contas que não tinham outra conexão visível se elas postassem esse tipo de link com frequência.

Mesmo do ponto de vista da engenharia social, se você pudesse, de alguma maneira, encontrar alguém para lhe enviar um link para a página de alguém, eles estariam entregando sua identidade a você sem nem mesmo saber.

Moral da história… Cuidado com o que está publicando, você nunca sabe o que pode estar revelando sobre você.

#### 30

*   [Facebook](https://medium.com/tag/facebook)
*   [Doxing](https://medium.com/tag/doxing)
*   [Dox](https://medium.com/tag/dox)
*   [Osint](https://medium.com/tag/osint)
*   [Rastreamento](https://medium.com/tag/tracking)

#### 30 palmas

[![AccessOSINT](https://miro.medium.com/fit/c/160/160/1*CgVXB8IRbo4hTrA2l7PtZg.png)](https://medium.com/@osint?source=follow_footer--------------------------follow_footer-)

ESCRITO POR

[AccessOSINT](https://medium.com/@osint?source=follow_footer--------------------------follow_footer-)
-----------------------------------------------------------------------------------------------------

Segue

#### Inteligência de código aberto