---
title: 'Atualmente, os aplicativos Web sofrem de uma variedade de
vulnerabilidades.'
date: 2019-10-02T12:39:00+01:00
draft: false
---

Atualmente, os aplicativos Web sofrem de uma variedade de vulnerabilidades. O Cross Site Scripting (XSS) é uma das falhas de segurança de aplicativos da Web mais comuns, mas possivelmente a mais negligenciada. Ele ocupa a segunda posição no Top 10 dos 10 riscos de segurança de aplicativos da Web da OWASP para 2010.

O script entre sites é um tipo de problema de injeção no qual scripts maliciosos (vb, js etc.) são injetados em um site confiável. As falhas do XSS ocorrem sempre que um aplicativo obtém dados não confiáveis ​​(geralmente fornecidos pelo usuário) e os envia inválidos ou não codificados para um navegador da web. O XSS permite que os invasores executem scripts no navegador da vítima e o script mal-intencionado pode acessar cookies, tokens de sessão ou outras informações confidenciais retidas pelo navegador. Utilizados com esse site, eles podem até reescrever o conteúdo da página HTML. Basicamente, explora a confiança que um navegador cliente tem no site. No XSS, o usuário confia que o conteúdo exibido no navegador foi destinado ao site.[Orkut](http://en.wikipedia.org/wiki/Orkut "Orkut") .

Um exemplo de uma página vulnerável ao XSS:

O seguinte segmento de código no JSP (Java Server Pages) lê um ID do funcionário: empid, de uma solicitação HTTP e a exibe.

```
<% String empid = request.getParameter("empid"); %>  
...  
...  
Employee ID:  

```

O código acima funcionará corretamente se o empid contiver apenas texto alfanumérico padrão, mas se o empid tiver um valor que inclua script (js, vb etc.) ou meta-caracteres, o código (talvez malicioso) será executado pelo navegador da web.

Tipos de XSS:

Existem basicamente três tipos de falhas de XSS: refletidas, armazenadas e baseadas em DOM.

Refletido ou não persistente:

O script entre sites refletido é o tipo mais comum de falha do XSS encontrada nos aplicativos da web atualmente. Nesse tipo de falha, o código injetado é refletido no servidor da Web, como em um resultado de pesquisa, em uma mensagem de erro ou em qualquer outra resposta que inclua entrada completa ou parcial enviada ao servidor como parte da solicitação.

O atacante precisa entregar o ataque às vítimas por outra rota, como em uma mensagem de email ou em outro servidor da web. O invasor envia o link malicioso para a vítima e, quando a vítima é enganada a clicar em um link malicioso ou enviar um formulário especialmente criado (por meio da Engenharia Social etc.), o código injetado viaja para o servidor do aplicativo Web vulnerável, o que reflete o ataque de volta ao navegador da vítima. O navegador, em seguida, executa o código malicioso, que veio de um servidor "confiável".  

Armazenado ou Persistente:  

A vulnerabilidade XSS armazenada é uma variante mais devastadora de uma falha de script entre sites. No tipo de falha Armazenada, o invasor pode injetar código malicioso no aplicativo vulnerável e o código injetado é armazenado permanentemente nos servidores de destino (em um banco de dados, campo de comentário, log de visitante etc.) e, em seguida, exibido permanentemente nas páginas "normais" retornadas para outros usuários durante a navegação regular. O XSS persistente é bastante significativo quando comparado a outros tipos, pois o script malicioso de um invasor é renderizado automaticamente, sem a necessidade de segmentar individualmente as vítimas ou atraí-las para um site de terceiros. Essa é uma falha perigosa, pois qualquer dado recebido pelo aplicativo da Web vulnerável (via email, logs do sistema etc.) que pode ser controlado por um invasor pode se tornar um vetor de injeção. Um exemplo clássico seria um invasor deixando um script mal-intencionado no campo de comentários do blog de um aplicativo da web vulnerável para blogs. O script malicioso será executado nos navegadores dos usuários que visitarão o blog posteriormente.

Baseado em DOM:

DOM é uma especificação do World Wide Web Consortium (W3C), que define o modelo de objeto para representar estruturas XML e HTML. XSS baseado em DOM ou XSS tipo 0 é uma falha XSS em que a carga útil do ataque é executada como resultado da modificação do "ambiente" DOM ​​no navegador da vítima usado pelo script original do lado do cliente, para que o código do lado do cliente seja executado de uma maneira "inesperada". O XSS baseado em DOM não é resultado de vulnerabilidade em um script do lado do servidor, mas um tratamento inadequado dos dados fornecidos pelo usuário no JavaScript do lado do cliente. Como os outros tipos de vulnerabilidades XSS, o XSS baseado em DOM pode ser usado para roubar informações confidenciais ou invadir a conta do usuário. No entanto, é essencial entender que esse tipo de vulnerabilidade depende apenas do JavaScript e do uso inseguro de dados obtidos dinamicamente da estrutura do DOM.

[](https://www.blogger.com/null)Cenários de ataque

Alguns dos cenários de ataque de amostra são os seguintes[](https://www.blogger.com/null):

Script através de um link malicioso  

Nesse cenário, o invasor envia uma mensagem de email criada para uma vítima que contém um link (contendo script malicioso) como o mostrado aqui:

```
 [malicious code here>Click here](http://VulnerableSite.com/registration.php?clprofile=<script)  

```

Quando um usuário inocente clica nesse link, o URL é enviado para o VulnerableSite.com, incluindo o código malicioso. Como o servidor legítimo envia uma página de volta ao usuário, incluindo o valor de clprofile (perfil do cliente), o código malicioso será executado no navegador da web do cliente. A Figura 1 mostra a ilustração do ataque.

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/011012_1356_CrossSiteSc1.jpg)  

Figura 1. Ataque via e-mail

Seqüestro de sessão (roubo de cookie)

Muitos sites usam autenticação de usuário baseada em cookies e dependem apenas de cookies de sessão para autenticação entre solicitações HTTP individuais e, como os scripts do lado do cliente geralmente têm acesso a esses cookies, explorações simples de XSS podem roubar esses cookies. Nesse cenário, o invasor pode enviar um link malicioso ou armazenar um script malicioso em uma página (XSS armazenada) do site vulnerável. Quando a página maliciosa é exibida, o script malicioso é executado, coleta os cookies do usuário e envia uma solicitação ao site do invasor com os cookies coletados. Usando essa técnica, o invasor pode invadir a sessão do usuário e obter informações confidenciais, como mostra a Figura 2 .

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/011012_1356_CrossSiteSc2.jpg)  

Figura 2. Roubo de cookie e seqüestro de sessão

Como detectar se um site é vulnerável?

As falhas de script entre sites podem ser difíceis de identificar e remover de um aplicativo Web. A melhor prática para procurar falhas é realizar uma intensa revisão de código e procurar todos os locais em que a entrada do usuário por meio de uma solicitação HTTP possa entrar na saída HTML. Uma variedade de tags HTML diferentes (como , ,  etc.) pode ser usada para transmitir um JavaScript malicioso. As ferramentas do WebScanner como Burp Suite, WebInspect, Acunetix, Netsparker, Websecurify, NStalker etc. podem ser usadas para procurar essas vulnerabilidades da Web, mas, juntamente com o teste manual, como a maioria das ferramentas, apenas testam usando scripts comuns e ignoram diferentes codificações e ignoram técnicas ( descrito por RSnake: [http://ha.ckers.org/xss.html](http://ha.ckers.org/xss.html) ).

Como é diferente do CSRF (falsificação de solicitação entre sites)  

Muitas vezes, as pessoas confundem entre XSS e CSRF. Ambas as vulnerabilidades requerem métodos diferentes de exploração e proteção de aplicativos da web. A falsificação de solicitação entre sites ou a condução de sessões é um tipo de ataque que força o usuário final a executar ações maliciosas indesejadas sem o conhecimento ou a intenção do aplicativo Web no qual eles estão atualmente autenticados. O script entre sites é a capacidade de fazer um site exibir o conteúdo fornecido pelo usuário incorporado ao HTML / JavaScript. O CSRF explora a confiança que um site possui no navegador do usuário, diferente do XSS, que tira proveito da confiança que um navegador cliente possui no site. No CSRF, o site confia que a solicitação proveniente do navegador do usuário é pretendida por ele, enquanto no XSS o usuário confia que o conteúdo exibido no navegador foi destinado ao site.

Um exemplo de ataque de CSRF:

Um usuário, Bob está navegando em um fórum, onde outro usuário, Max postou uma mensagem. Esta mensagem é um link malicioso criado por Max, contendo um elemento de imagem HTML e refere uma ação no site do banco de Bob.

```
![](http://Bobbank.com/withdraw?acc_name=bob&amount=1000&to=max)  

```

Observe aqui que não há um arquivo de imagem real, mas se o cookie de autenticação de Bob (para o site do banco) não tiver expirado, então, quando o navegador de Bob tentar carregar a imagem, ele enviará automaticamente o formulário de retirada (junto com o cookie de Bob), assim, uma transação não intencional da conta de Bob ocorrerá.

Atenuando a falha
-----------------

As técnicas a seguir podem ser usadas para proteger contra esta vulnerabilidade

Usuário final: um usuário pode tomar a seguinte medida para se proteger do XSS
------------------------------------------------------------------------------

Desativando scripts
-------------------

Embora os designers da Web 2.0 e do Ajax sejam a favor do uso de JavaScript, alguns aplicativos da Web são gravados para (opcionalmente) operar completamente sem a necessidade de scripts do lado do cliente. Isso permite que os usuários desabilitem o script em seus navegadores antes de usar o aplicativo. Dessa forma, os usuários não seriam suscetíveis a ataques XSS, mesmo que scripts potencialmente maliciosos do lado do cliente sejam inseridos sem codificação em uma página.

Alguns navegadores ou plug-ins de navegadores podem ser configurados para desativar scripts do lado do cliente por domínio. Uma dessas soluções para o Firefox e outros navegadores baseados no Gecko é o complemento [NoScript de](http://en.wikipedia.org/wiki/NoScript "NoScript") código aberto que, além de sua capacidade de desativar scripts por domínio, também fornece proteção anti-XSS, mesmo quando os scripts estão ativados, mas também pode diminuir a funcionalidade do site. Essa técnica pode ser usada pelo usuário para sua proteção contra a vulnerabilidade.

Final do desenvolvedor: as seguintes técnicas podem ser usadas pelos desenvolvedores para liberar o aplicativo Web do XSS
-------------------------------------------------------------------------------------------------------------------------

Codificação de saída
--------------------

O principal mecanismo de defesa para interromper o XSS é a codificação ou saída de saída contextual. "Escapar" é uma técnica usada para garantir que os caracteres sejam tratados como dados, não como caracteres relevantes para o analisador do intérprete. É o principal meio de garantir que dados não confiáveis ​​não possam ser usados ​​para transmitir um ataque de injeção. Não há mal em escapar dos dados corretamente - eles ainda serão renderizados no navegador corretamente. O escape simplesmente permite que o intérprete saiba que os dados não devem ser executados e, portanto, impede que os ataques funcionem. Um código de exemplo no JSP para escape é mostrado abaixo.

  

```
public static String encode(String data)  
{  
     final StringBuffer newbuf = new StringBuffer();  
     final char\[\] chars = data.toCharArray();  
     for (int i = 0; i < chars.length; i++)  
{  
     newbuf.append("&").append((int) chars\[i\]);  
}  
     return newbuf.toString();  
}  

```

Quando uma entrada maliciosa no formato de script é inserida através do campo nome de usuário, a página vulnerável exibe um pop-up de alerta, conforme exibido na Figura 3 . Isso pode levar ao seqüestro de sessões, desfiguração do lado do cliente etc.

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/011012_1356_CrossSiteSc3.jpg)  

Figura 3: O pop-up ocorre para uma entrada semelhante na página vulnerável

Para uma entrada semelhante na página segura, não há efeito, pois a saída é codificada, como mostra a Figura 4 .

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/011012_1356_CrossSiteSc4.jpg)  

Figura 4: Nenhum efeito de entrada maliciosa na Página segura

Validando entrada não confiável
-------------------------------

A validação de entrada é simplesmente verificar a validade de cada entrada. Isso pode significar muitas coisas, mas, no caso mais simples, significa verificar o tipo e o comprimento dos dados. Nesse caso, pode significar verificar entradas comuns com script, suas variações e formas codificadas. Se a validação de entrada for feita corretamente em todo o código do site, eliminaremos um grande número de vulnerabilidades, como XSS e SQL Injection, etc. A validação de entrada deve ser realizada em qualquer dado recebido que não seja controlado e confiável. Isso inclui dados fornecidos pelo usuário, dados de terceiros ou outros locais.

Antes de usar os dados recebidos não confiáveis, siga as etapas a seguir:

*   Normalize  
    URL / UTF-7 / Unicode / US-ASCII / etc. decodificar os dados recebidos.
*   Verificação do conjunto de caracteres  
    Verifique se os dados contêm apenas caracteres esperados.
*   Restrições de comprimento (mínimo / máximo)  
    Verifique se os dados estão dentro de um número mínimo e máximo restrito de bytes.
*   Formato dos dados  
    Verifique se a estrutura dos dados é consistente com o que é esperado.

(Fonte: [Jeremiah Grossman](http://jeremiahgrossman.blogspot.com/2007/01/input-validation-or-output-filtering.html/) )

Implementando WAFs

Os firewalls têm sido amplamente utilizados para proteger os servidores implementando regras baseadas em rede; da mesma forma, um firewall de aplicativo da web (WAF) é um dispositivo, plug-in de servidor ou filtro que aplica um conjunto de regras a uma conversa HTTP. Geralmente, essas regras abrangem ataques comuns, como XSS (Cross-site Scripting) e SQL Injection. Ao personalizar as regras para o aplicativo, muitos ataques podem ser identificados e bloqueados. O esforço para executar essa customização pode ser significativo e precisa ser mantido à medida que o aplicativo é modificado. Alguns exemplos comuns de WAF são ModSecurity e PHPIDS.

API de segurança  

ESAPI (A API de segurança corporativa da OWASP) é uma biblioteca de controle de segurança de aplicativos da web de código aberto e gratuita desenvolvida pela OWASP, que facilita aos programadores a criação de aplicativos de menor risco. As bibliotecas ESAPI foram projetadas para facilitar a adaptação dos programadores à segurança dos aplicativos existentes. As bibliotecas ESAPI também servem como uma base sólida para novos desenvolvimentos.  
Os módulos e seu lugar na arquitetura do aplicativo podem ser vistos na Figura 5 .

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/011012_1356_CrossSiteSc5.jpg)  

Figura 5. Módulos[ ESAPI ](https://resources.infosecinstitute.com/cross-site-scripting-xss/www.owasp.org)([ www.owasp.org ](https://resources.infosecinstitute.com/cross-site-scripting-xss/www.owasp.org))

Conclusão

Com o advento da Web 2.0, os aplicativos da Web melhoraram significativamente a funcionalidade e a apresentação, mas, ao mesmo tempo, o fator de risco também aumentou. A implementação ignorante dessas tecnologias afeta a funcionalidade e o comportamento do aplicativo, o que representa um risco significativo para o usuário final. O risco se torna ainda mais grave quando outra falha em um componente é fundida com ele (neste caso, XSS + CSRF). Portanto, para garantir a segurança, os desenvolvedores e os usuários finais devem tomar as devidas precauções ao lidar com aplicativos da Web.

Referências para leitura adicional

*   [https://www.owasp.org/index.php/Cross-site\_Scripting\_(XSS)](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS))
    

*   [http://ha.ckers.org/xss.html](http://ha.ckers.org/xss.html)
    

*   [http://www.steve.org.uk/Security/XSS/](http://www.steve.org.uk/Security/XSS/)
    

*   [http://noscript.net/features](http://noscript.net/features)