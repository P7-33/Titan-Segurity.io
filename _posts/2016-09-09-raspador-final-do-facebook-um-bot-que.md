---
title: 'Raspador final do Facebook - um bot que raspa quase tudo no perfil de
um usuário do Facebook'
date: 2019-12-03T12:32:00+01:00
draft: false
---

Raspador final do Facebook - um bot que raspa quase tudo no perfil de um usuário do Facebook, incluindo todas as postagens / status públicos disponíveis na linha do tempo do usuário, fotos carregadas, fotos marcadas, vídeos, lista de amigos e suas fotos de perfil
=======================================================================================================================================================================================================================================================================

[ 12 DIAS ATRÁS  17:51](https://www.kitploit.com/2019/11/ultimate-facebook-scraper-bot-which.html "Quinta-feira, 21 de novembro de 2019")[ ZION3R](https://www.kitploit.com/2019/11/ultimate-facebook-scraper-bot-which.html "Zion3R")

[](https://www.blogger.com/null)  

[![](https://1.bp.blogspot.com/-XP4GRwvdIHw/XdNYvIlKquI/AAAAAAAAQ4E/6fmCNDqBmjcKJhF6kP0tpoYRkrRzaBvDQCNcBGAsYHQ/s640/Ultimate-Facebook-Scraper_19_screenshot.png)](https://1.bp.blogspot.com/-XP4GRwvdIHw/XdNYvIlKquI/AAAAAAAAQ4E/6fmCNDqBmjcKJhF6kP0tpoYRkrRzaBvDQCNcBGAsYHQ/s1600/Ultimate-Facebook-Scraper_19_screenshot.png)

  
Ferramentas que **automatizam** suas interações nas mídias sociais para coletar postagens, fotos, vídeos, amigos, seguidores e muito mais no Facebook.  

  

**Características**  
Um bot que raspa quase tudo sobre o perfil de um usuário do Facebook, incluindo  

*   fotos enviadas
*   fotos marcadas
*   vídeos
*   lista de amigos e suas fotos de perfil (incluindo seguidores, seguidores, amigos de trabalho, amigos de faculdade etc.)
*   e todas as postagens / status públicos disponíveis na linha do tempo do usuário.

[  
](https://www.blogger.com/null)[![](https://1.bp.blogspot.com/-SaOn3uzljH8/XOjbmoStJpI/AAAAAAAAPGo/7Tbg3FbTrjIkIPWkihcrESbZyaRLtrdPgCLcBGAs/s1600/brave_05.png)](https://bit.ly/browser_brave)  

A melhor coisa sobre esse raspador é que os dados são raspados em um formato organizado para que possam ser usados ​​para fins educacionais / de pesquisa pelos pesquisadores. Além disso, esse raspador não usa a API Graph do Facebook, portanto, não há problemas de limitação de taxa como tal.  
**Esta ferramenta está sendo usada por milhares de desenvolvedores semanalmente e estamos muito surpresos com essa resposta! Obrigado pessoal!**  
Para detalhes sobre como **citar / referenciar** esta ferramenta para sua pesquisa, consulte a seção 'Citação' abaixo.  
  
**Nota**  
Na sua essência, esta ferramenta usa xpaths de **'divs'** para extrair dados deles. Como o Facebook continua atualizando seu site com frequência e os 'divs' são alterados. Consequentemente, temos que atualizar as divs de acordo para raspar os dados corretamente.  
Os desenvolvedores desta ferramenta dedicaram muito tempo e esforço no desenvolvimento e manutenção da ferramenta mais importante por um bom tempo. **Para manter viva essa incrível ferramenta, precisamos do apoio de seus geeks.**  
O código é bastante intuitivo e fácil de entender, para que você possa atualizar os xpaths relevantes no código quando sentir que tentou vários perfis e os dados não estiverem sendo raspados para nenhum deles (é uma dica de que o Facebook atualizou seus site) e gere uma solicitação de recebimento. Isso é algo fácil de fazer. Obrigado!  
  
**Amostra**  

  

[![](https://1.bp.blogspot.com/-BZ-c7ezD4wE/XdNY3GfaEbI/AAAAAAAAQ4I/I2PvaxLFCIofbeuD86CywOoKjZ7Nbtt6QCNcBGAsYHQ/s640/Ultimate-Facebook-Scraper_18_main.png)](https://1.bp.blogspot.com/-BZ-c7ezD4wE/XdNY3GfaEbI/AAAAAAAAQ4I/I2PvaxLFCIofbeuD86CywOoKjZ7Nbtt6QCNcBGAsYHQ/s1600/Ultimate-Facebook-Scraper_18_main.png)

**Captura de tela**  

  

[![](https://1.bp.blogspot.com/-t5jFK84FK8U/XdNY8QTTbyI/AAAAAAAAQ4M/TdZEavyJhbs9f6hMXqSDAJz8bmoEujVHwCNcBGAsYHQ/s640/Ultimate-Facebook-Scraper_19_screenshot.png)](https://1.bp.blogspot.com/-t5jFK84FK8U/XdNY8QTTbyI/AAAAAAAAQ4M/TdZEavyJhbs9f6hMXqSDAJz8bmoEujVHwCNcBGAsYHQ/s1600/Ultimate-Facebook-Scraper_19_screenshot.png)

  
  
**Instalação de ****uso**  
Você precisará instalar a versão mais recente do[ Google Chrome](https://www.google.com/chrome/ "Google Chrome") . Além disso, você precisa instalar omódulo[ selênio](https://www.kitploit.com/search/label/Selenium "selênio") também usando  
```
pip install selenium
```Execute o código usando o Python 3. Além disso, o código é multiplataforma e é testado no Windows e Linux. A ferramenta usa a versão mais recente do [Chrome Web Driver](http://chromedriver.chromium.org/downloads "Driver da Web do Chrome") . Coloquei o driver da web junto com o código, mas se essa versão não funcionar, substitua o driver da web chrome pelo mais recente.  
  
**Como executar**  
Há um arquivo chamado "input.txt". Você pode adicionar quantos perfis desejar no seguinte formato com cada link em uma nova linha:  
```
https://www.facebook.com/andrew.ng.96  
https://www.facebook.com/zuck
```Certifique-se de que o link contenha apenas o nome de usuário ou o número de identificação no final e não outras coisas. Verifique se está no formato mencionado acima.  
Nota: Existem dois modos para baixar as Fotos do perfil de amigos e as Fotos do usuário: Tamanho grande e Tamanho pequeno. Você pode alterar as seguintes variáveis. Por padrão, eles são definidos como Fotos de tamanho pequeno, porque é realmente rápido, enquanto o Modo de tamanho grande leva tempo, dependendo do número de fotos a serem baixadas.  
```
# whether to download the full image or its thumbnail (small size)  
# if small size is True then it will be very quick else if its False then it will open each photo to download it  
# and it will take much more time  
friends_small_size = True  
photos_small_size = True
```  
**Autores**  
Você pode entrar em contato conosco em nossos perfis do LinkedIn:  
**Haris Muneer**  
**Hassaan Elahi**  
  
  

**[Baixar Ultimate-Facebook-Scraper](https://github.com/harismuneer/Ultimate-Facebook-Scraper "Baixar Ultimate-Facebook-Scraper")**