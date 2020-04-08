---
title: 'OSINT: CAPTURA AVANÇADA Tinder'
date: 2019-11-26T01:31:00+01:00
draft: false
---

[![Aprenda todas as coisas](https://static1.squarespace.com/static/5689e180a2bab85273822321/t/57cf7c9eebbd1adbaf1ed244/1560225699523/?format=1000w)](https://www.learnallthethings.net/)
========================================================================================================================================================================================

Recursos OSINT

*   [HOME - APRENDA TODAS AS COISAS](https://www.learnallthethings.net/)


============================================================================================

**OSINT: CAPTURA AVANÇADA DE PAVIO**
====================================

![Conferência OSMOSIS 2017 em Myrtle Beach, Carolina do Sul](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1507658528927-GNDBERVVBHMYXT81B8EL/ke17ZwdGBToddI8pDm48kK60W-ob1oA2Fm-j4E_9NQB7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z4YTzHvnKhyp6Da-NYroOW3ZGjoBKy3azqku80C789l0kD6Ec8Uq9YczfrzwR7e2Mh5VMMOxnTbph8FXiclivDQnof69TlCeE0rAhj6HUpXkw/IMG_3372.jpg?format=750w)

Conferência OSMOSIS 2017 em Myrtle Beach, Carolina do Sul






















==========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

**OSMOSE**
==========

Em outubro passado, tive o prazer de falar sobre o OSINT em investigações de mídia social na conferência [OSMOSIS](https://www.osmosiscon.com/) em Myrtle Beach, Carolina do Sul. Durante essa palestra, demonstrei o uso de um [emulador Android](https://www.bluestacks.com/) para falsificar minha localização e fazer reconhecimento no aplicativo de namoro Tinder. Conversando com alguns dos pesquisadores da conferência, descobri que a configuração de algumas pessoas para esse processo é interrompida pelas atualizações de aplicativos. Portanto, este post compartilha os detalhes da configuração do meu emulador e explora os métodos OSINT para capturar evidências do Tinder.














================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

**CONFIGURAÇÃO DO EMULADOR PARA TINDER**
========================================

Esta é a configuração geral que estou usando e os números de versão dos programas:

![Bluestacks Versão 3 específicos](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515591472210-ZC0Z6DRIM208239H4U0F/ke17ZwdGBToddI8pDm48kKNuRL0cf4OMekHNyVr3TxxZw-zPPgdn4jUwVcJE1ZvWEtT5uBSRWt4vQZAgTJucoTqqXjS3CfNDSuuf31e0tVE_jcp5Q5ykyBJN8l63ERCltgWNZ9cZttzvzD9KSvMwspf2csZlcAx1_wS6tVfnuFQ/BS+version.JPG?format=500w)

Bluestacks Versão 3 específicos

Tinder app APK versão 7.5.2

Aplicativo falso GPS gratuito versão 4.3.2 

Pode haver outras variáveis ​​que podem afetar seus resultados (como o sistema operacional host e alguns dos drivers de serviços do google do emulador), mas, como em 11/01/18, minha configuração ainda está funcionando em uma conta padrão gratuita do Tinder. Eu recomendo evitar atualizações no seu sistema de captura depois de obter uma variação funcional.














=========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

**USANDO O EMULADOR**
=====================

O uso do sistema é simples quando você instala os aplicativos no emulador.

Ao executar o Bluestacks, inicie o aplicativo 'Fake GPS Free' e altere o local para qualquer outro lugar:

![Bom dia para uma rápida viagem à Holanda](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515592305364-ZYRTLLQ6XBYY87OE4WF6/ke17ZwdGBToddI8pDm48kF3GQae-47ekGtHk54NeYuJ7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z5QPOohDIaIeljMHgDF5CVlOqpeNLcJ80NK65_fV7S1Ua2ATFhh7YyISx5g_oO4KGAaS8SSX6Bp9hOw6vbBmxGzoZT0dmrDnLzkDHG7TUYW2w/FakeGPS.JPG?format=750w)

Bom dia para uma rápida viagem à Holanda

Clicar no botão laranja 'play' (Reproduzir) no canto inferior direito da tela iniciará o farol de localização do emulador. Em seguida, lançamos o aplicativo Tinder:

![Tinder appblur.jpg](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515592852935-GIXL3HOXU2RWL3PNP5UC/ke17ZwdGBToddI8pDm48kFCMwbRiDd0qYJYN6-1EAo4UqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8GRo6ASst2s6pLvNAu_PZdLwKcoejbCN47i7rcU72toYzd4j6q-LDD2_xHGrqBvXmJro3BtiToxHuVSuvzaGIXs/Tinder+appblur.jpg?format=750w)

Agora estamos vendo usuários ativos no aplicativo a até 3 km de Amsterdã (os filtros de distância e pessoas podem ser alterados no aplicativo Tinder)

![Tinder settings.JPG](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515593888305-LECIZHZVZ7MP5BHUV5LI/ke17ZwdGBToddI8pDm48kFcoH1sbWBGblbUlmIuo61ZZw-zPPgdn4jUwVcJE1ZvWQUxwkmyExglNqGp0IvTJZUJFbgE-7XRK3dMEBRBhUpygOO9PHwQqSosE7BgeTRPqbqwHHzGOfrxxwVcByIzniypO32sWsWqqqsI1PQO5hEw/Tinder+settings.JPG?format=750w)


















===================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

**EXPORTANDO EVIDÊNCIA**
========================

Para preservação, sempre há capturas de tela do sistema operacional host (como eu uso para esta entrada do blog). O Bluestacks também possui sua própria capacidade de captura de tela, mas meu método preferido de obter evidências como essa é a captura com o [Wireshark](https://www.wireshark.org/) . O Wireshark é uma ferramenta de captura de pacotes de rede com uma ampla variedade de usos da infosec. O que eu gosto em usá-lo para a captura do Tinder é a capacidade de exportar imagens em massa rapidamente. O Wireshark pode parecer esmagador para aqueles que não o usaram, mas depois que você o instala, o processo é bastante simples para despejar todas as fotos de perfil que você encontra na sua sessão de navegação no Tinder.

![Depois que um pacote é capturado no Wireshark, vá para: Arquivo - Exportar Objetos - HTTP](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515596958772-AL82JHMDT0MSHY19NAMF/ke17ZwdGBToddI8pDm48kOSfJwEHeHOBMKyMHtxz5e0UqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYxCRW4BPu10St3TBAUQYVKcyarE_CSv74BhYpoC6s3t8ZhcqFqe-imiwm-xL5Ymx0LgYSqBITO0DxmKUnilUJ79/wireshark+export.JPG?format=750w)

Depois que um pacote é capturado no Wireshark, vá para: Arquivo - Exportar Objetos - HTTP

O Wireshark oferece a opção de 'Salvar tudo'

![exportobjects.JPG](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515597135471-12OC2E5M8BAIIGZWTXOY/ke17ZwdGBToddI8pDm48kBNdE-I6FBPdKrBtQLBvJPUUqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYxCRW4BPu10St3TBAUQYVKctDkUWMgmc57a24nDCk4ENtjo_B9Oq3L9k8Yk98Sy-Kn3kgULK4Vuvbo7qo59hLoE/exportobjects.JPG?format=750w)

Agora você tem um diretório das fotos de perfil que você navegou na sua sessão do emulador

![photo capture.JPG](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515597218937-0SYO8I1LL3DHAYK0GPZ1/ke17ZwdGBToddI8pDm48kISWbSf1k2WlYhTnu4YJpscUqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYy7Mythp_T-mtop-vrsUOmeInPi9iDjx9w8K4ZfjXt2doalZnAQwEOvJVBSJFGCRa2atuFxee92wUWzHSj9GOmh3WUfc_ZsVm9Mi1E6FasEnQ/photo+capture.JPG?format=750w)


















====================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

**USANDO A VERSÃO DA WEB**
==========================

No final de 2017, o Tinder lançou totalmente a versão do aplicativo com base no navegador. Portanto, se você não deseja configurar um emulador, também pode fazer o reconhecimento a partir do seu navegador. (a falsificação de local pode ser mais desafiadora no navegador)

![Tinder de dentro de um navegador Chrome](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515623469936-RXMKWRZG5CVZA6ZOH0Z9/ke17ZwdGBToddI8pDm48kA8-r_U-7U2-yUJ8YkK7UOIUqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYy7Mythp_T-mtop-vrsUOmeInPi9iDjx9w8K4ZfjXt2dmzbGXYJcA0q49azAeB2fLnOZp1IzRnfNdNvCtLA9L0xJvwGh1qtNWvMhYKnvaKhbA/browser.JPG?format=750w)

Tinder de dentro de um navegador Chrome

Por estar em um navegador da Web, agora temos a capacidade de executar uma ferramenta de captura de navegador, como o [Nimbus Screenshot](https://chrome.google.com/webstore/detail/nimbus-screenshot-screen/bpconcjcammlapcogcnnelfmaeghhagj?hl=en) ou o [Hunchly](https://www.hunch.ly/) . Também temos acesso total a coisas como visualizar a origem da página e usar [pesquisas de imagem reversa,](https://github.com/IVMachiavelli/OSINT_Team_Links#image-search) se necessário, para OSINT.  














====================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

**PESQUISA REVERSA DE IMAGENS**
===============================

Sem chamar um alvo inocente, vamos encontrar alguém que possa estar usando uma foto de perfil falsa. As contas em que normalmente encontro fotos falsas geralmente contêm apenas uma foto no perfil ... como esta:

![Bitcoin lulz ... legal.](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515683027859-MV9TZ6K3N1SLMGJOXAXB/ke17ZwdGBToddI8pDm48kNzXoJ3SWM2nmQbavQrMia9Zw-zPPgdn4jUwVcJE1ZvWEtT5uBSRWt4vQZAgTJucoTqqXjS3CfNDSuuf31e0tVF8khDXpMfxRxgL-B2Bm3uGGRT2-cdS15GbK45SyFC_lVxcyQviE7z7AywoJQDN0Tg/Jennifer.JPG?format=500w)

Bitcoin lulz ... legal.

Novamente, a vantagem que temos ao trabalhar em um navegador é uma análise OSINT profunda. Clique com o botão direito do mouse diretamente na imagem do homem na piscina e selecione 'Inspecionar'

![Visualização Dev Tools da página do Tinder no Chrome](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515683467706-G2C8H7V4P4959HECEXXQ/ke17ZwdGBToddI8pDm48kDD0bBXohJrWhiyIweHslnsUqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYy7Mythp_T-mtop-vrsUOmeInPi9iDjx9w8K4ZfjXt2dl4A23l1nx-MA9txNJbkMGRc3rIdmTJXHwDma3H1tXzPoRwB-dUGsSquCnVTFQcaRg/Dev.jpg?format=750w)

Visualização Dev Tools da página do Tinder no Chrome

Agora clique com o botão direito do mouse no link na parte superior da janela Elementos, que é o link direto para a foto do perfil. Selecione 'Copiar endereço do link'. Abra uma nova guia do navegador e cole o link.

![link direto.JPG](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515683674062-RKTH73GG96DFAHUU72NN/ke17ZwdGBToddI8pDm48kBluUOy1Hste1MlBLIVPqoUUqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYxCRW4BPu10St3TBAUQYVKc3v2eLHb_IQfMxAoYJyNdg7upBOvYm7d8E-0aywiJp606Ns-UJEirFUq2bRGcsBrF/direct+link.JPG?format=750w)

A partir daí, você pode executar sua ferramenta de análise de fotos de sua escolha. É fácil clicar com o botão direito do mouse e "pesquisar esta imagem no google"

![Pesquisa no google por image.JPG](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515684304798-1XHKPDNNUVVJK3ETO32P/ke17ZwdGBToddI8pDm48kN8_U3wMJvNO2t8P62Bv2cVZw-zPPgdn4jUwVcJE1ZvWQUxwkmyExglNqGp0IvTJZamWLI2zvYWH8K3-s_4yszcp2ryTI0HqTOaaUohrI8PIXH6Ic9xKYMgZmgp4nuIf-9GcouRRN2N3zQvSj7eqqR4KMshLAGzx4R3EDFOm1kBS/Search+google+for+image.JPG?format=750w)

Também podemos colar o link direto em uma ferramenta de imagem reversa como o [Tineye](https://tineye.com/) :

![https://tineye.com/search/5688cefe20f1a8f5bbdde741bf8c9db1f3491c67/](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515684361286-K98AKOPGI6CL7QTUS3HR/ke17ZwdGBToddI8pDm48kAJEma-ScfRDt1s4W1g13VdZw-zPPgdn4jUwVcJE1ZvWQUxwkmyExglNqGp0IvTJZamWLI2zvYWH8K3-s_4yszcp2ryTI0HqTOaaUohrI8PIlhYfCtsomB9Q4lkImvy5NySpypCNXkkSUaVxv6iX3iwKMshLAGzx4R3EDFOm1kBS/Tineye.JPG?format=750w)

https://tineye.com/search/5688cefe20f1a8f5bbdde741bf8c9db1f3491c67/

Nas duas pesquisas, sua aparente 'Jennifer' tirou a foto de um dos vários sites que estava usando uma imagem da Getty Images.

![https://www.istockphoto.com/ca/photo/friends-enjoying-next-to-the-edge-of-pool-with-beer-gm801526672-129967143](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515684457618-XB57SPE9ABZ31X1K3WAL/ke17ZwdGBToddI8pDm48kF9_gN-nrr34KXZgQwvPQy0UqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYxCRW4BPu10St3TBAUQYVKcJ9yih8k8heuwm_kqEzAe9YbC0QYsIhcPS2ERMAZYlJFcES1TXnqB7ZWLsWMmiuWa/stock+photo.JPG?format=750w)

https://www.istockphoto.com/ca/photo/friends-enjoying-next-to-the-edge-of-pool-with-beer-gm801526672-129967143

Assim como o meme 'Disloyal Boyfriend', podemos encontrar mais imagens da mesma série:

![Talvez seja Jennifer ... provavelmente não.](https://images.squarespace-cdn.com/content/v1/5689e180a2bab85273822321/1515686336325-BURIYUSF92LU8Z8BWE9M/ke17ZwdGBToddI8pDm48kJggs40jQ-wk9q5EuEa9gtxZw-zPPgdn4jUwVcJE1ZvWQUxwkmyExglNqGp0IvTJZUJFbgE-7XRK3dMEBRBhUpwbZzQn5Tf-P6OdejuPCTFfjyUvI68cZ3pVKb3Q06F9CE84smwwaKzm8v_P5SGpHqE/maybe+jennifer.JPG?format=750w)

Talvez seja Jennifer ... provavelmente não.

Espero que você tenha gostado dessa visão geral das técnicas OSINT para o Tinder. Se você tiver algum comentário ou suas próprias técnicas para compartilhar, envie-me uma [mensagem](https://twitter.com/baywolf88) no Twitter [@ baywolf88](https://twitter.com/baywolf88)

Happy OSINTing

  


=============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================