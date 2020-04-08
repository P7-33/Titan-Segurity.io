---
title: 'Observar, detectar e investigar redes ODIN'
date: 2019-11-26T01:25:00+01:00
draft: false
---

ODIN
====

[](https://github.com/chrismaddalena/ODIN?source=post_page-----bee58de48e05----------------------#observe-detect-and-investigate-networks)Observar, detectar e investigar redes
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Versão Python](https://camo.githubusercontent.com/bf11e1cdac43e53d4aea9c234045ee2256a04fd4/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f507974686f6e2d332e372d627269676874677265656e2e737667)](https://github.com/chrismaddalena/ODIN/blob/master) [![Licença](https://camo.githubusercontent.com/43ec89e2ae73c78601cd6e5d01fd7118d608fed2/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d425344332d6461726b7265642e737667)](https://github.com/chrismaddalena/ODIN/blob/master)

[![ODIN](https://github.com/chrismaddalena/ODIN/raw/master/ODIN.png)](https://github.com/chrismaddalena/ODIN/raw/master/ODIN.png)

### [](https://github.com/chrismaddalena/ODIN?source=post_page-----bee58de48e05----------------------#current-version-v200-huginn)Versão atual: v2.0.0 "Huginn"

ODIN é uma ferramenta Python para automatizar a coleta de informações, a descoberta de ativos e os relatórios. Lembre-se, verifique o ramo de desenvolvimento quanto à borda sangrenta e feedback é bem-vindo!

Veja o wiki do GitHub para detalhes e instruções de instalação e configuração.

[](https://github.com/chrismaddalena/ODIN?source=post_page-----bee58de48e05----------------------#what-can-odin-do)O que o ODIN pode fazer?
-------------------------------------------------------------------------------------------------------------------------------------------

O ODIN tem como objetivo automatizar as tarefas básicas de reconhecimento usadas pelas equipes vermelhas para descobrir e coletar dados sobre ativos de rede, incluindo domínios, endereços IP e sistemas voltados para a Internet. O principal recurso do ODIN é o gerenciamento de dados e relatórios. Os dados são organizados em um banco de dados e, opcionalmente, esse banco de dados pode ser convertido em um relatório HTML ou em um banco de dados gráfico Neo4j para visualização dos dados.

O ODIN realiza isso em várias fases:

### [](https://github.com/chrismaddalena/ODIN?source=post_page-----bee58de48e05----------------------#phase-1---asset-discovery)Fase 1 - Descoberta de ativos

*   Colete informações básicas da organização de fontes como o banco de dados de marketing Full Contact.
*   Verifique os certificados DNS Dumpster, Netcraft e TLS para descobrir subdomínios para os domínios fornecidos.
*   Resolva domínio e subdomínios para endereços IP por meio de conexões de soquete e registros DNS.
*   Colete informações de todos os endereços IP, como dados de propriedade e organização, do RDAP, whois e outras fontes de dados.
*   Pesquise domínios e pesquise endereços IP no Shodan para coletar dados adicionais, como sistemas operacionais, banners de serviço e portas abertas.
*   Verifique a possibilidade de aquisições e frente de domínio com os domínios e subdomínios.

### [](https://github.com/chrismaddalena/ODIN?source=post_page-----bee58de48e05----------------------#phase-2---employee-discovery)Fase 2 - Descoberta de funcionários

*   Colete endereços de email e nomes de funcionários da organização de destino.
*   Vincule funcionários a perfis de mídia social por meio de mecanismos de pesquisa e da API do Twitter.
*   Verifique cruzadamente os endereços de e-mail descobertos com Have I Been Pwned de Troy Hunt.

### [](https://github.com/chrismaddalena/ODIN?source=post_page-----bee58de48e05----------------------#phase-3---cloud-and-web-services)Fase 3 - Serviços na nuvem e na Web

*   Procure arquivos e PDFs do Office no domínio de destino, faça o download e extraia metadados.
*   Pesquise baldes do AWS S3 e espaços digitais do oceano usando palavras-chave relacionadas à organização.
*   Faça capturas de tela dos serviços da Web descobertos para uma rápida revisão rápida dos serviços.

### [](https://github.com/chrismaddalena/ODIN?source=post_page-----bee58de48e05----------------------#phase-4---reporting)Fase 4 - Relatórios

*   Salve todos os dados em um banco de dados SQLite3 para permitir que os dados sejam facilmente consultados.
*   Gere um relatório HTML usando consultas SQL padrão para simplificar a leitura dos dados em um navegador da web.
*   Crie um banco de dados gráfico do Neo4j que vincule todas as entidades descobertas (endereços IP, domínios, subdomínios, portas e certificados) juntamente com os relacionamentos (por exemplo, RESOLVES\_TO, HAS\_PORT).

No final de tudo isso, você terá várias maneiras de navegar e visualizar os dados. Mesmo uma consulta simples do Neo4j como `MATCH (n) RETURN n`(exibir tudo) pode criar um gráfico fascinante do perímetro externo da organização e simplificar a visualização de como os ativos estão vinculados. As [páginas wiki do Neo4j](https://github.com/chrismaddalena/ODIN/wiki/Graphing-Data) contêm melhores exemplos de consulta.