---
title: "[ディストリビューション エージェント セキュリティ] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.security.DA.f1"
helpviewer_keywords: 
  - "[ディストリビューション エージェント セキュリティ] ダイアログ ボックス"
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# [ディストリビューション エージェント セキュリティ]
   **ディストリビューション エージェント セキュリティ** ] ダイアログ ボックスでは、ディストリビューション エージェントを実行する Windows アカウントを指定することができます。 ディストリビューション エージェントは、プッシュ サブスクリプションのディストリビューターと、プル サブスクリプションのサブスクライバーで動作します。  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントとも呼ばれる、 *プロセス アカウント*, エージェント プロセスがこのアカウントで実行されるので、します。 ダイアログ ボックスで使用できる追加オプションは、次に示すアクセスの方法によって異なります。  
  
-   サブスクリプションの新規作成ウィザードからこのダイアログ ボックスにアクセスする場合、サブスクライバー (プッシュ サブスクリプション) またはディストリビューター (プル サブスクリプション) への接続を作成するディストリビューション エージェントのコンテキストを指定することもできます。 Windows アカウントを借用するかのコンテキストでは、接続を確立できる、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の指定したアカウントです。  
  
-   ダイアログ ボックスにアクセスすると、 **サブスクリプションのプロパティ** ] ダイアログ ボックスで、ディストリビューション エージェントが、[プロパティ] をクリックして接続を作成するコンテキストを指定 (**...**) で、 **サブスクライバー接続** または **ディストリビューター接続** そのダイアログ ボックスの行。 アクセスの詳細については、 **サブスクリプションのプロパティ** ダイアログ ボックスを参照してください [プッシュ サブスクリプション プロパティの変更を表示および](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) とする方法: [ビューとプル サブスクリプションのプロパティの変更](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)します。  
  
 各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## オプション  
 **[プロセス アカウント]**  
 ディストリビューション エージェントが実行される Windows アカウントを入力します。  
  
-   プッシュ サブスクリプションでは、アカウントには次のことが必要です。  
  
    -   最低のメンバーである、 **db_owner** ディストリビューション データベースの固定データベース ロール。  
  
    -   パブリケーション アクセス リスト (PAL) のメンバーになれる。  
  
    -   スナップショット共有の読み取り権限を持っている。  
  
    -   サブスクリプションが非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーの場合、サブスクライバーの OLE DB プロバイダーのインストール ディレクトリへの読み取り権限を持つ。  
  
-   プル サブスクリプションの場合、アカウントには少なくともメンバーであるは **db_owner** サブスクリプション データベースの固定データベース ロール。  
  
 接続を作成するときにプロセス アカウントを借用する場合、追加の権限が必要です。 参照してください、 **ディストリビューターへの接続** と **サブスクライバーへの接続** 以下のセクションでします。  
  
 **プロセス アカウント** に対するプル サブスクリプションを指定できません [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], のインスタンスで、ディストリビューション エージェントが実行されないので、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]です。  
  
 **パスワード** と **パスワードの確認**  
 Windows アカウントのパスワードを入力します。  
  
 **[ディストリビューターに接続]**  
 プッシュ サブスクリプションの場合、ディストリビューターへの接続は常にで指定されたアカウントを借用して作成、 **プロセス アカウント** テキスト ボックスです。  
  
 プル サブスクリプションの場合、ディストリビューション エージェントは、ディストリビューターに接続で指定されたアカウントを偽装することによって作成するかどうかを選択して、 **プロセス アカウント** テキスト ボックスまたはを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。  
  
 接続に使用する Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントには次のことが必要です。  
  
-   PAL のメンバーである。  
  
-   スナップショット共有の読み取り権限を持っている。  
  
 **[サブスクライバーに接続]**  
 プル サブスクリプションの場合、サブスクライバーへの接続は常にで指定されたアカウントを借用して作成、 **プロセス アカウント** テキスト ボックスです。  
  
 プッシュ サブスクリプションでは、次のように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーと非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーのオプションが異なります。  
  
-    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバー: ディストリビューション エージェントはで指定されたアカウントを偽装することによって、サブスクライバーへ接続を作成する必要があるかどうかを選択して、 **プロセス アカウント** テキスト ボックスまたはを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。  
  
     Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーへの接続に使用するアカウントには少なくともメンバーであるは **db_owner** サブスクリプション データベースの固定データベース ロール。  
  
-   非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーでは、ディストリビューション エージェントがサブスクライバーに接続するときに使用する必要のあるサブスクライバーでデータベース ログインを指定します。 ログインは、サブスクリプション データベースにオブジェクトを作成するための十分な権限を持つ必要があります。 以外の構成の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーを参照してください [非 SQL Server サブスクライバーのサブスクリプションを作成](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)します。  
  
 **[追加の接続オプション]**  
 非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーのみです。 接続文字列の形式で、サブスクライバーの任意の接続オプションを指定します (Oracle では追加のオプションは不要)。 各オプションはセミコロンで区切る必要があります。 次は、IBM DB2 接続文字列の例です (読みやすくするために改行されています)。  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 文字列内のオプションの多くは、接続する DB2 サーバーに固有のものですが、 **Process Binary as Character** オプションは常に **False**に設定する必要があります。 サブスクリプション データベースを識別するため、 **Initial Catalog** オプションに値が必要です。 詳細については、次を参照してください。 [IBM DB2 サブスクライバー](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)します。  
  
## 参照  
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  