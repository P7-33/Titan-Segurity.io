---
title: 'Cinco maneiras de identificar e-mails de phishing Um guia atualizado
sobre o reconhecimento de golpes baseados em email'
date: 2019-10-04T13:17:00+01:00
draft: false
---

Cinco maneiras de identificar e-mails de phishing
=================================================

Um guia atualizado sobre o reconhecimento de golpes baseados em email
---------------------------------------------------------------------

[

![Gabor Szathmari](https://miro.medium.com/fit/c/48/48/1*wq6OURHLVVme_NrQ1QKWig.png)

](https://medium.com/@gszathmari?source=post_page-----9466f4dd2c04----------------------)

[Gabor Szathmari](https://medium.com/@gszathmari?source=post_page-----9466f4dd2c04----------------------)

Segue

[1 de outubro de 2018](https://medium.com/iron-bastion/five-ways-to-detect-phishing-emails-9466f4dd2c04?source=post_page-----9466f4dd2c04----------------------) · 6 min de leitura

![](https://miro.medium.com/max/30/1*DXR6sgpQQYK82xq000xesg.jpeg?q=20)

![](https://miro.medium.com/max/3714/1*DXR6sgpQQYK82xq000xesg.jpeg)

Como os e-mails de phishing vêm em diferentes formas e formatos, não existe uma bala de prata para identificar um e-mail de phishing. No entanto, há uma coleção de bandeiras vermelhas que você deve procurar antes de clicar em uma nova mensagem. Aqui está o nosso guia atualizado, ajudando você a identificar os mais recentes golpes baseados em email.

O que é phishing? Phishing é um ataque cibernético normalmente realizado por email. Em suma, os cibercriminosos pretendem induzir suas vítimas a clicar em um link ou anexo, dar sua senha ou pedir dinheiro, fingindo ser um serviço online legítimo, cliente, amigo ou colega.

Indicadores fortes de que um email pode ser enganoso
====================================================

Embora outras pistas estejam disponíveis, os seguintes indicadores são os principais métodos para decidir se um email é genuíno ou não:

*   ["); text-decoration-line: none;" target="\_blank">](https://postmarkapp.com/guides/spf)Violações do ["); text-decoration-line: none;" target="\_blank">Sender Policy Framework (SPF)](https://postmarkapp.com/guides/spf) .
*   O nome de exibição e / ou endereço de e-mail do remetente são falsificados.
*   O endereço IP do servidor SMTP de envio não pertence à organização do remetente.
*   Os links clicáveis ​​da Web não levam a um "domínio confiável".
*   O email apresenta um anexo de arquivo não solicitado.

\# 1 Violações da Sender Framework Policy (SPF)
===============================================

Se o nome de domínio do remetente especificar os hosts SMTP permitidos em um registro SPF e o servidor de email de recebimento suportar pesquisas de SPF, o servidor de email sinalizará os emails que violam a política do SPF. Normalmente, esses e-mails são rejeitados ou movidos automaticamente para sua pasta de spam.

A ["); text-decoration-line: none;" target="\_blank">taxa de adoção de registros SPF é de cerca de 50%, de](https://www.tablix.org/~avian/blog/archives/2016/02/some_spf_statistics/) acordo com um relatório de 2016. No entanto, os provedores de hospedagem de e-mail mal configurados podem manter esses e-mails na sua Caixa de entrada.

![](https://miro.medium.com/max/30/0*nOEOv5fZWM5iGM-K.jpg?q=20)

![](https://miro.medium.com/max/1744/0*nOEOv5fZWM5iGM-K.jpg)

O domínio 'time.kz' não designa 'mail.globalreservation.com' como remetente permitido (Fonte: Iron Bastion)

Para descobrir se um email suspeito violou a política do SPF, ["); text-decoration-line: none;" target="\_blank">visualize os cabeçalhos da mensagem](https://www.arclab.com/en/kb/email/how-to-read-and-analyze-the-email-header-fields-spf-dkim.html) e procure o `Received-SPF`cabeçalho. Se o status for 'falhar', o email poderá ser uma tentativa de phishing.

\# 2 Nome do remetente e / ou endereço de e-mail falsificado
============================================================

Existem ["); text-decoration-line: none;" target="\_blank">dois métodos comuns de falsificação de remetentes que os](https://blog.ironbastion.com.au/email-impersonation-scams-phishing-what-your-staff-can-do/) cibercriminosos usam. Para fins ilustrativos, digamos que a pessoa que queremos representar é `Peter File`e seu endereço de email é `peter.file@brasseye.com`:

1.  Email Address Spoofing : endereço de e-mail de Pedro e seu nome são ambos falsificado em um e-mail de entrada para que o remetente parece ser: `Peter File` .
2.  Display Name Spoofing : nome Apenas de Pedro é falsificado, mas não o endereço de e-mail: `Peter File` .

Para verificar o remetente de um email, basta observar o nome e o endereço de email do remetente no seu cliente de email. O nome do remetente e o endereço de email devem ser exibidos por padrão. Por outro lado, os smartphones podem não exibir o endereço de e-mail do remetente. Nesse caso, você pode revelar o endereço subjacente mantendo pressionado o nome do remetente.

A falsificação de endereço de email (método 1) tornou-se mais difícil para os cibercriminosos por causa do SFP. Se você vir um e-mail de um nome e endereço de e-mail que você sabe que acaba no spam, deixe-o lá, é provável que ele tenha falhado na validação do SPF e tenha sido movido para lá de propósito.

\# 3 O endereço IP de envio não pertence à organização remetente
================================================================

Outro indicador de um email de phishing é o endereço IP de envio (ou nome do host) do servidor de email SMTP de envio.

Se o email for enviado `peter.file@brasseye.com`, é seguro presumir que o servidor SMTP remetente esteja intimamente associado à organização remetente (por exemplo `smtp01.brasseye.com`) ou a um provedor de hospedagem de email respeitável, como o Office 365 ou o G Suite. Caso o email seja enviado de um endereço IP ou nome de host associado a países e organizações não relacionados, o email poderá não ser genuíno.

![](https://miro.medium.com/max/30/0*PEc2u0angVPEYa6N.jpg?q=20)

![](https://miro.medium.com/max/1560/0*PEc2u0angVPEYa6N.jpg)

Essa notificação falsa do PayPal foi enviada através de um servidor SMTP não relacionado e apresenta a técnica de falsificação de nome para exibição (Fonte: Iron Bastion)

Você pode procurar o endereço IP e o nome do host do servidor SMTP de envio (assim como muitas outras propriedades) com a combinação do ["); text-decoration-line: none;" target="\_blank">MX Toolbox Email Header Analyzer](https://mxtoolbox.com/Public/Tools/EmailHeaders.aspx) e um serviço como o ["); text-decoration-line: none;" target="\_blank">ipinfo.io](http://ipinfo.io/) . Se você usa o Microsoft Outlook, existe um utilitário útil chamado ["); text-decoration-line: none;" target="\_blank">Message Header Analyzer](https://appsource.microsoft.com/en-us/product/office/WA104005406) que também pode mostrar essas informações.

\# 4 Links clicáveis ​​levam a domínios desconhecidos ou não relacionados
=========================================================================

Links da Web incorporados em e-mails podem levar a sites enganosos que hospedam páginas de login falsas ou explorações de navegadores da Web. É crucial inspecionar um link da Web antes de clicar passando o mouse sobre eles (em um computador desktop) ou pressionando-o com um smartphone.

Se o email aparentemente vier de um provedor confiável como o PayPal, o link da web deve estar apontando para um nome de domínio associado ao domínio.

![](https://miro.medium.com/max/30/0*pufVY9-_CFsBA5sB.jpg?q=20)

![](https://miro.medium.com/max/1662/0*pufVY9-_CFsBA5sB.jpg)

Este e-mail deveria vir do Mailgun.com, mas o link da Web nos levaria a um domínio não relacionado (Fonte: Iron Bastion)

Infelizmente, as grandes empresas tendem a registrar variantes de domínio confusas de suas marcas. Por exemplo, _support @ paypal-techsupport \[.\] Com_ é um endereço de email legítimo pertencente à equipe de suporte técnico do comerciante do PayPal. Outros domínios como _paypal-knowledge \[.\] Com_ e _paypal-community \[.\] Com_ também são domínios legítimos também usados ​​pelo PayPal.

Também é importante não se deixar enganar por subdomínios que são usados ​​enganosamente para mascarar o verdadeiro nome de domínio de um link da web. Da direita para a esquerda, o nome de domínio em um URL está entre os últimos “/” e os primeiros 2 ou 3 pontos completos. Qualquer coisa de ambos os lados é irrelevante, mas geralmente é usada por criminosos cibernéticos para fazer um link parecer mais autêntico.

![](https://miro.medium.com/max/30/1*ZeoeDM9-fz9Qb0H7C0K3fA.png?q=20)

![](https://miro.medium.com/max/356/1*ZeoeDM9-fz9Qb0H7C0K3fA.png)

Um link da web enganoso feito para parecer uma página de login do eBay. O nome do domínio verdadeiro é destacado. (Fonte: Bastião de Ferro)

\# 5 Anexos de arquivo
======================

Trate todos os emails que chegam com um anexo de arquivo não solicitado que chegue como suspeito. Anexos de arquivo maliciosos geralmente são disfarçados de currículos, faturas e recibos. Ao contrário do que se pensa, os anexos maliciosos não são arquivos executáveis ​​(".exe"), mas documentos como Word (".doc", ".docx" e ".rtf") e Portable Document Format (".pdf") arquivos.

![](https://miro.medium.com/max/30/1*1U-Ux0wBhsdsmJ0fz0M9Vg.png?q=20)

![](https://miro.medium.com/max/640/1*1U-Ux0wBhsdsmJ0fz0M9Vg.png)

O ransomware pode chegar em documentos do Word como este (Fonte: Ars Technica)

Se você receber um email com um anexo de arquivo que não esperava, confirme com o remetente em um canal fora de banda (como uma ligação telefônica) que o anexo de arquivo é genuíno ou abra-o em um ambiente sandbox como uma máquina virtual .

Os visualizadores de documentos on-line em PDF e Word incorporados no Gmail e no Office 365 também podem neutralizar conteúdo prejudicial, pois esses visualizadores não oferecem suporte a conteúdo ativo com abuso frequente, como macros JavaScript e Office.

Indicadores fracos de que um email pode ser uma tentativa de phishing
=====================================================================

Essas dicas costumam circular na internet, mas, infelizmente, ["); text-decoration-line: none;" target="\_blank">são ineficazes,](https://blog.ironbastion.com.au/why-outdated-anti-phishing-advice-leaves-you-exposed-part-1/) pois o nível de sofisticação dos cibercriminosos aumentou com o tempo:

*   E-mails mal escritos - Os cibercriminosos podem contar com serviços de revisão como o ["); text-decoration-line: none;" target="\_blank">Fiverr](https://www.fiverr.com/gigs/proofreading) para obter a gramática correta ou, no que se tornou uma prática comum em phishing, os invasores simplesmente clonam notificações por e-mail comuns de marcas e empresas conhecidas.
*   Saudações não personalizadas - 'Caro senhor' em vez de 'Caro Peter'. Mesmo boletins legítimos muitas vezes não recebem a saudação corretamente.
*   Sensação de urgência e consequências de longo alcance se uma ação específica não for tomada - Por exemplo, você será bloqueado de uma conta ou a conta será excluída se você não efetuar o login nas próximas 24 horas.

Em resumo, trate todos os emails com uma suspeita que vem com um link da Web, anexo de arquivo ou uma solicitação para executar uma ação. Se você ainda estiver em dúvida, entre em contato com seu amigo ou colegas para confirmação ou deixe o email sem resposta.

Sobre o Bastião de Ferro
========================

O Iron Bastion é o especialista em phishing e segurança cibernética da Austrália. Fornecemos consultoria em segurança cibernética com soluções especializadas para combater o phishing. Nossa equipe é formada por profissionais qualificados em segurança cibernética, e todos os nossos funcionários e operações estão sediados na Austrália.

["); text-decoration-line: none;" target="\_blank">_Entre em contato conosco_](https://www.ironbastion.com.au/contact-us/)_ para uma consulta gratuita sobre segurança cibernética ou inscreva-se hoje em _["); text-decoration-line: none;" target="\_blank">_nossos serviços gerenciados_](https://www.ironbastion.com.au/services/managed-cybersecurity-services)_ ._

* * *

_Publicado originalmente em _["); text-decoration-line: none;" target="\_blank">_blog.ironbastion.com.au_](https://blog.ironbastion.com.au/p/0565702d-22b4-43df-8ed4-65a6a54f4c95/)_ . Este artigo foi co-escrito com _["); text-decoration-line: none;" target="\_blank">_Nicholas Kavadias_](https://www.linkedin.com/in/nicholas-kavadias/)_ ._

[

Bastião de ferro
----------------

](https://medium.com/iron-bastion?source=post_sidebar--------------------------post_sidebar-)

#### Somos especialistas em phishing e segurança cibernética da Austrália

Segue

#### 176

#### 

[Alguns direitos reservados](http://creativecommons.org/licenses/by/4.0/)

*   [Segurança](https://medium.com/tag/security)
*   [Phishing](https://medium.com/tag/phishing)
*   [Consciência de segurança](https://medium.com/tag/security-awareness)
*   [Cíber segurança](https://medium.com/tag/cybersecurity)
*   [O email](https://medium.com/tag/email)

#### 176 palmas

[

![Gabor Szathmari](https://miro.medium.com/fit/c/80/80/1*wq6OURHLVVme_NrQ1QKWig.png)

](https://medium.com/@gszathmari?source=follow_footer--------------------------follow_footer-)

ESCRITO POR

[Gabor Szathmari](https://medium.com/@gszathmari?source=follow_footer--------------------------follow_footer-)
--------------------------------------------------------------------------------------------------------------

Segue

#### Especialista em segurança cibernética e entusiasta da privacidade digital