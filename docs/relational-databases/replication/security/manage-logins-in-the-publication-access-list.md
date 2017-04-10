---
title: "パブリケーション アクセス リストのログインの管理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "logins [SQL Server replication], publication access list"
  - "publications [SQL Server replication], publication access lists"
  - "publication access list (PAL)"
  - "PAL (publication access list)"
  - "ログイン [SQL Server レプリケーション], 管理"
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# パブリケーション アクセス リストのログインの管理
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、パブリケーション アクセス リストのログインを管理する方法について説明します。 パブリケーションへのアクセスは、パブリケーション アクセス リスト (PAL) によって制御されます。 ログインおよびグループの PAL への追加および PAL からの削除を実行できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
-   **パブリケーション アクセス リストのログインを管理するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   PAL にログインを追加する前に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインをパブリケーション データベースのデータベース ユーザーに関連付ける必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーション アクセス リスト (PAL) を使用して、 **パブリケーション アクセス リスト** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ログインを管理する] ダイアログ ボックス。 このダイアログ ボックスにアクセスする方法の詳細については、次を参照してください。 [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### PAL のログインを管理するには  
  
1.   **パブリケーション アクセス リスト** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、使用、 **追加**, 、**削除**, 、および **すべて削除** ボタンを追加および PAL のログインおよびグループを削除します。 削除しないでください **distributor_admin** PAL からです。 このアカウントはレプリケーションで使用されます。  
  
    > [!NOTE]  
    >  リモート ディストリビューターを使用する場合、PAL 内のアカウントは、パブリッシャーとディストリビューターの両方で使用できる必要があります。 このアカウントは、どちらのサーバーでも定義されているドメイン アカウントまたはローカル アカウントにする必要があります。 両方のログインに関連付けられているパスワードは、同じにする必要があります。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### PAL に登録されているグループおよびログインを表示するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_help_publication_access](../../../relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql.md)します。 **@publication**には、パブリケーション名を指定します。 これで、PAL のグループおよびログインに関する情報が表示されます。  
  
#### グループおよびログインを PAL に追加するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_grant_publication_access](../../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)します。 **@publication**には、パブリケーション名を指定します、 **@login**には、追加するログインまたはグループの名前を指定します。  
  
#### グループおよびログインを PAL から削除するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_revoke_publication_access](../../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)します。 **@publication**には、パブリケーション名を指定します、 **@login**には、削除するログインまたはグループの名前を指定します。  
  
## 参照  
 [Manage Logins in the Publication Access List](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション トポロジのセキュリティ保護](../../../relational-databases/replication/security/secure-a-replication-topology.md)   
 [パブリッシャーのセキュリティ保護](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  