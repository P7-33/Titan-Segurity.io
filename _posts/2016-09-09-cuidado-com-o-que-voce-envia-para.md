---
title: 'Cuidado com o que você envia para a Lixeira!'
date: 2019-11-10T13:54:00+01:00
draft: false
---

Cuidado com o que você envia para a Lixeira!
============================================

Por: [Marcos Henrique](https://www.100security.com.br/author/marcos-henrique/ "Marcos Henrique") | 292 Views | [2 Respostas](https://www.100security.com.br/lixeira/#comments "Comente sobre Cuidado com o que você envia para a Lixeira!")

[](https://www.blogger.com/null)

Como sabe é comum utilizar a Lixeira do Windows para dispensar aqueles arquivos que não utilizamos mais. Porém devemos redobrar a atenção para o que enviamos para a Lixeira, pois a Segurança dos seus dados ou da sua empresa podem estar em jogo.

Durante um PenTest você pode ate considerar incluir este passo a passo para tentar extrair informações sensíveis sobre o ambiente e auxiliar a equipe de Segurança a fim de melhorar a abordagem e os pontos de atenção durante a campanha de Conscientização sobre Segurança da Informação para os funcionários.

**Observações:**

*   Administradores de Redes **não** armazenem senhas em arquivos de texto, planilhas. (Utilize um Cofre de Senhas).

**01 Passo**

Para extrair os arquivos da Lixeira de um usuário é necessário descobrir qual SID do usuário. Para isso basta executar o comando:

```
C:\100security>wmic useraccount get Name,SID
```

![](https://www.100security.com.br/wp-content/uploads/2019/11/trash-01.png)

**02 Passo**

Entre no diretório** C:\\** e execute o comando **dir /a** para exibir todas as pastas ocultas.

Você deve encontrar a pasta: $Recycle.Bin

*   C:\\$Recycle.Bin – Windows Vista ou Superior
*   C:\\RECYCLER – Windows NT/2000/XP
*   C:\\RECYCLED – Windows 95/98/ME 

```
C:\100security>cd \  
  
C:\>dir /a
```

![](https://www.100security.com.br/wp-content/uploads/2019/11/trash-02.png)

**03 Passo**

Acesse a pasta $Recycle.Bin e digite o comando **dir /a** para visualizar a pasta correspondente ao usuário que deseja acessar.

No meu exemplo a pasta S-1-5-21-1214171880-496033222-1301047076-1010 correspondente ao usuário 100security (01 Passo).

```
C:\>cd $Recycle.Bin  
  
C:\$Recycle.Bin> dir /a
```

![](https://www.100security.com.br/wp-content/uploads/2019/11/trash-03.png)

**04 Passo**

Acesse a pasta S-1-5-21-1214171880-496033222-1301047076-1010 e visualize os arquivos que estão armazenados na **Lixeira** utilizando o comando **dir**.

**Observações:**

*   $Ixxxxx – São os Metadados dos arquivos.
*   $Rxxxxx – São os arquivos com conteúdo. 

```
C:\$Recycle.Bin>cd S-1-5-21-1214171880-496033222-1301047076-1010  
  
C:\$Recycle.Bin\S-1-5-21-1214171880-496033222-1301047076-1010>
```

![](https://www.100security.com.br/wp-content/uploads/2019/11/trash-04.png)

**05 Passo**

Criei uma pasta (ex: **Lixeira**) para copiar todo os arquivos da Lixeira do usuário, em seguida realize a **copia** dos arquivos que iniciam com $R.

```
C:\$Recycle.Bin\S-1-5-21-1214171880-496033222-1301047076-1010>md C:\100security\Lixeira  
  
C:\$Recycle.Bin\S-1-5-21-1214171880-496033222-1301047076-1010>copy $R* C:\100security\Lixeira
```

![](https://www.100security.com.br/wp-content/uploads/2019/11/trash-05.png)

**06 Passo**

Acesse a pasta (ex: **C:\\100security\\Lixeira**) para visualizar os arquivos.

![](https://www.100security.com.br/wp-content/uploads/2019/11/trash-06.png)

Arquivo de texto com Senhas: $ROI2QI3.txt

![](https://www.100security.com.br/wp-content/uploads/2019/11/trash-07.png)

**Atenção!!!**

Com as informações encontradas na Lixeira um usuário mal intencionado poderia ter acesso aos servidores da sua empresa.

![](https://www.100security.com.br/wp-content/uploads/2019/11/trash-08.png)

[](https://www.blogger.com/null)

Categorias: [Análise de Vulnerabilidade](https://www.100security.com.br/category/analise-de-vulnerabilidade/), [Ferramentas de Relatórios](https://www.100security.com.br/category/ferramentas-de-relatorios/), [Pentest](https://www.100security.com.br/category/pentest/), [Todos os Artigos](https://www.100security.com.br/category/todos-os-artigos/), [Windows](https://www.100security.com.br/category/windows/) | Palavras-chave: [$Recycle.Bin](https://www.100security.com.br/tag/recycle-bin/), [Lixeira](https://www.100security.com.br/tag/lixeira/), [Pentest](https://www.100security.com.br/tag/pentest/), [Recovery](https://www.100security.com.br/tag/recovery/), [Recuperação de Dados](https://www.100security.com.br/tag/recuperacao-de-dados/), [Recuperar](https://www.100security.com.br/tag/recuperar/), [Recycled](https://www.100security.com.br/tag/recycled/), [Recycler](https://www.100security.com.br/tag/recycler/), [Senhas](https://www.100security.com.br/tag/senhas/), [Trash](https://www.100security.com.br/tag/trash/)

Autor
-----

[![Avatar](https://www.100security.com.br/wp-content/plugins/user-avatar/user-avatar-pic.php?src=https://www.100security.com.br/wp-content/uploads/avatars/8/1531676592-bpfull.jpg&w=110&id=8&random=1531676592)](https://www.100security.com.br/author/marcos-henrique/)

### [Marcos Henrique](https://www.100security.com.br/author/marcos-henrique/)

Marcos Henrique é pós-graduado em Segurança da Informação, é o desenvolvedor do site 100security.com.br, autor dos livros Nagios – Monitoramento de Redes e ownCloud – Crie sua Própria Nuvem publicados pela editora Ciência Moderna.