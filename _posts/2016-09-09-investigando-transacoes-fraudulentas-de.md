---
title: 'Investigando transações fraudulentas de Bitcoin usando OSINT'
date: 2019-09-25T19:09:00+01:00
draft: false
---

  

===

[![Gagan Jain Bommaiah Satish](https://miro.medium.com/fit/c/48/48/1*Oi6yBWNvFKW124TKnTUI0A.jpeg)](https://medium.com/@gags.gk?source=post_page-----90d861dc9e17----------------------)

[Gagan Jain Bommaiah Satish](https://medium.com/@gags.gk?source=post_page-----90d861dc9e17----------------------)

Segue

[25 de março](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17?source=post_page-----90d861dc9e17----------------------) · 6 min. De leitura

Resumo: Atualmente, existem centenas de portais de troca de criptomoedas, tornando-se ainda mais fácil com novos aplicativos chegando e aplicativos antigos reunindo mais público a cada dia. Os reguladores estão lutando com o modo de fornecer segurança ao consumidor com essas empresas, além de agora olhar para trocas descentralizadas e empresas ou bancos de criptografia para trocas de criptografia.

Falaremos sobre como investigar melhor com ferramentas OSINT e informações de código aberto para encontrar o melhor caminho para o invasor ou fraude por trás do ato.

O que são bitcoins e criptomoedas?
==================================

A criptomoeda principalmente Bitcoin foi fundada por Satoshi Nakamoto, que cita “O _Bitcoin é um novo sistema de caixa eletrônico que usa uma rede ponto a ponto para evitar gastos duplos. É completamente descentralizado, sem servidor ou autoridade central. _” ["); text-decoration-line: none;" target="\_blank">\[1\]](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17#_ftn1)

Após anos de falha na abordagem diferente do sistema financeiro centralizado, as funções e a segurança têm suas limitações, como gastar o mesmo usuário duas vezes ou o sistema faz a transação duas vezes, existem métodos para superar aqueles como usar um verificador de terceiros que também armazena logs de transações e IDs para verificar cada transação A Satoshi desenvolveu uma nova forma de sistema de negociação baseado em pares que é descentralizado e tem o poder de superar as limitações dos sistemas centralizados. Esse novo sistema usa uma rede blockchain para transacionar e processar dados.

Na rede bitcoin, os dados de cada transação conterão as chaves públicas do remetente e do destinatário, basicamente, seus endereços de carteira e a quantidade de moedas a serem transferidas. O remetente deve assinar a transação com essa chave privada. Cada transação realizada é registrada no livro público da blockchain. Depois que a transação é assinada, os dados não são transferidos diretamente para a rede e vão para os “mineradores” Em uma rede de criptomoedas, apenas os mineradores podem confirmar as transações resolvendo enigmas criptográficos. Eles aceitam transações, as marcam como legítimas e as espalham pela rede. Posteriormente, cada nó da rede o adiciona ao seu banco de dados e a transação é confirmada, tornando-se imperdoável e irreversível e um minerador recebe uma recompensa, mais as taxas de transação. Agora em 2019, de acordo com o investimento. com existem cerca de 2525 tipos diferentes de criptomoedas. Os valores de mercado de cada criptomoeda variam de acordo com a disponibilidade de mineração e a dificuldade de decifrar o quebra-cabeça criptográfico. Em março de 2019, o bitcoin custa cerca de US $ 3995,5 por BTC.["); text-decoration-line: none;" target="\_blank">\[2\]](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17#_ftn2)

Então você deu uma solução para um problema, então qual é o problema?

Como essas criptomoedas fornecem anonimato como parte do protocolo de segurança, elas podem ser usadas por golpistas de lavagem de dinheiro, financiamento ao terrorismo, tráfico de drogas e mais transações fraudulentas antiéticas / ilegais, pois essas transações tendem a permanecer anônimas e não há muitas tecnologias criadas para investigar esses plataformas.

O que é o CryptoCurrency OSINT?

Inteligência de código aberto (OSINT) são dados coletados de fontes publicamente disponíveis para serem usados ​​em um contexto de inteligência; esses dados são usados ​​por pesquisadores, jornalistas, testadores de caneta e hackers para encontrar informações confidenciais publicamente disponíveis no Clearnet e no Darknet.

INVESTIGANDO TRANSACÇÕES COM BITCOINS USANDO OSINTPs Nota: este artigo é apenas para fins educacionais e não haverá explicação sobre como rastrear a origem do proprietário da carteira. Diferentemente das transações monetárias normais que não são registradas em nenhum lugar que enviaram quem os bitcoins monetários estão registrados em um razão público, discutiremos como encontrar essas informações usando o osint.

Ferramentas usadas para análise:

\- BlockChain Explorer: ["); text-decoration-line: none;" target="\_blank">https://www.blockchain.com/explorer](https://www.blockchain.com/explorer)

\- Navegador Tor: ["); text-decoration-line: none;" target="\_blank">https://www.torproject.org/](https://www.torproject.org/)

\- Maltego - ["); text-decoration-line: none;" target="\_blank">https://www.paterva.com/web7/buy/maltego-clients/maltego-ce.php](https://www.paterva.com/web7/buy/maltego-clients/maltego-ce.php)  
\-Wallet Explorer - ["); text-decoration-line: none;" target="\_blank">https://www.walletexplorer.com](https://www.walletexplorer.com/)

1\. URL do site que carregava o endereço de bitcoin do estado islâmico de financiamento: jihadlove5xhyfw3.onion

2\. Use o endereço Onion para alimentar a transformação maltego e procurar informações sobre blockchain. Encontramos um endereço de bitcoin anexado a este site '1FmLPWZjru5njVmzDV9wgzJqnMbuJUWs36'

![](https://miro.medium.com/max/30/1*MhGtYBkwXfsZLZCbk77fNg.png?q=20)

![](https://miro.medium.com/max/631/1*MhGtYBkwXfsZLZCbk77fNg.png)

3\. O plugin Maltego fornece endereços de diferentes carteiras nas quais as transações foram registradas no livro público e também os hashes das transações.

Podemos dizer várias coisas apenas de um endereço de bitcoin, como:

\- Quantas transações ocorreram

\- De onde veio o dinheiro e quanto

\- Para onde foi enviado dinheiro e quanto

\- Um cronograma histórico de transações

\- E outros endereços de bitcoin associados nessa carteira

4\. Usamos o blockchain explorer para ver as transações

Agora vemos que existem cerca de 6 transações para esta carteira. Totalizando em torno de 0,0915088 BTC.

![](https://miro.medium.com/max/30/1*duPEZO4RXbnGpfcgE5BVIA.png?q=20)

![](https://miro.medium.com/max/624/1*duPEZO4RXbnGpfcgE5BVIA.png)

Se eu navegar pelas Transações, vemos uma certa transação começando com '6b172'

![](https://miro.medium.com/max/30/1*mKJD90G1BXI_V99TriW2Ug.png?q=20)

![](https://miro.medium.com/max/624/1*mKJD90G1BXI_V99TriW2Ug.png)

Todas as outras transações são normais com o endereço do remetente e o endereço do destinatário, mas essa transação '6b172' possui vários endereços do remetente porque o remetente usou uma técnica de evasão ao registro usando algo chamado 'bitcoin-mixer', esses misturadores preenchem o livro com falsas e endereços de carteira reais para que a transação real não seja notada. O endereço final da carteira pode ser um endereço de serviço do misturador de bitcoin ou o endereço do anonimizador.

Para muitos fornecedores na dark web, um serviço de mixagem, ou código de criptomoeda, garante o anonimato, pois embaralha essencialmente os endereços e os pagamentos feitos - perfeito para fornecedores e golpistas ilegais, não para aplicação da lei. ["); text-decoration-line: none;" target="\_blank">\[3\]](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17#_ftn3)

Existe algum serviço de misturadores que eu possa encontrar facilmente?  
Sim, existe: ["); text-decoration-line: none;" target="\_blank">https://bestmixer.io](https://bestmixer.io/)

O que eles fazem?

Quando você envia suas moedas para o BestMixer.io, elas são inseridas em um conjunto de moedas junto com as de outros depositantes. Nosso mecanismo de mistura então tomba suas moedas junto com as outras na piscina. As moedas que você recebe como resultado são compostas de bits de várias fontes diferentes, embaralhando assim suas origens e tornando-as não rastreáveis ["); text-decoration-line: none;" target="\_blank">\[4\]](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17#_ftn4)

Voltando à nossa investigação, vamos a um site chamado: ["); text-decoration-line: none;" target="\_blank">https://www.walletexplorer.com,](https://www.walletexplorer.com/) onde podemos ver a análise detalhada dessa carteira de bitcoin, saldo da conta, data e ID da transação.

![](https://miro.medium.com/max/30/1*_1GQTSK1P7GRL7zVzXpSxQ.png?q=20)

![](https://miro.medium.com/max/624/1*_1GQTSK1P7GRL7zVzXpSxQ.png)

Quando analisamos cada transação no bitcoin explorer, podemos ver o ID da transação '4156' e '91cf' o proprietário da carteira: '1FmLPWZjru5njVmzDV9wgzJqnMbuJUWs36' está encaminhando os bitcoins para mais uma conta, esse pode ser o endereço principal da carteira do proprietário.

Esta conta tem um total de 472.438.23785633 BTC, totalizando cerca de 1,87,57,92,401,50 Dólar dos Estados Unidos

![](https://miro.medium.com/max/30/1*ooemD1M7V9hA_AMOwgpYug.png?q=20)

![](https://miro.medium.com/max/624/1*ooemD1M7V9hA_AMOwgpYug.png)

Conclusão: O endereço do Bitcoin é usado por um grupo de fraude chamado 'DOUBLE YOUR BITCOINS', que é um famoso esquema de bitcoin e aqui podemos concluir que dizer o endereço principal que encontramos pertence a esse grupo. Agora que identificamos os golpistas, podemos realizar ataques de engenharia social ou qualquer outro teste de penetração no email ou número de telefone encontrado nas informações de código aberto.

O site do fundo da jihad usa esses programas fraudulentos para gerar receita, também conhecidos por usar campanhas de ransomware para obter financiamento.

["); text-decoration-line: none;" target="\_blank">\[1\] ](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17#_ftnref1)["); text-decoration-line: none;" target="\_blank">https://cointelegraph.com/bitcoin-for-beginners/what-are-cryptocurrencies#history](https://cointelegraph.com/bitcoin-for-beginners/what-are-cryptocurrencies#history)

["); text-decoration-line: none;" target="\_blank">\[2\] ](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17#_ftnref2)["); text-decoration-line: none;" target="\_blank">https://www.investing.com/crypto/currencies](https://www.investing.com/crypto/currencies)

["); text-decoration-line: none;" target="\_blank">\[3\] ](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17#_ftnref3)["); text-decoration-line: none;" target="\_blank">https://medium.com/coinmonks/tracing-an-offshore-bank-and-a-dark-web-service-using-the-blockchain-an-osint-investigation-a1000251c3ec](https://medium.com/coinmonks/tracing-an-offshore-bank-and-a-dark-web-service-using-the-blockchain-an-osint-investigation-a1000251c3ec)

["); text-decoration-line: none;" target="\_blank">\[4\] ](https://medium.com/@gags.gk/investigating-fraudulent-bitcoin-transactions-using-osint-90d861dc9e17#_ftnref4)["); text-decoration-line: none;" target="\_blank">https://bestmixer.io/en/how.](https://bestmixer.io/en/how)

Twitter: ["); text-decoration-line: none;" target="\_blank">https://twitter.com/g4g5j41n](https://twitter.com/g4g5j41n) / ["); text-decoration-line: none;" target="\_blank">https://twitter.com/Bunyy9](https://twitter.com/Bunyy9)

#### 53

*   [Bitcoin](https://medium.com/tag/bitcoin)
*   [Osint](https://medium.com/tag/osint)
*   [Criptomoeda](https://medium.com/tag/cryptocurrency)
*   [Investigação](https://medium.com/tag/investigation)
*   [Cíber segurança](https://medium.com/tag/cybersecurity)

#### 53 palmas

[![Gagan Jain Bommaiah Satish](https://miro.medium.com/fit/c/80/80/1*Oi6yBWNvFKW124TKnTUI0A.jpeg)](https://medium.com/@gags.gk?source=follow_footer--------------------------follow_footer-)

ESCRITO POR

[Gagan Jain Bommaiah Satish](https://medium.com/@gags.gk?source=follow_footer--------------------------follow_footer-)
----------------------------------------------------------------------------------------------------------------------

Segue

#### Entusiasta da CyberSecurity e Investigador Forense

[

Ver respostas (1)

](https://medium.com/p/90d861dc9e17/responses/show?source=follow_footer--------------------------follow_footer-)