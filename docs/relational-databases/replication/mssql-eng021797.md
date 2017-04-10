---
title: "MSSQL_ENG021797 | Microsoft Docs"
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
  - "MSSQL_ENG021797 エラー"
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG021797
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21797|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|'%s' は次の形式の有効な Windows ログインにしてください: 'MACHINE\Login' または 'DOMAIN\Login'。 '%s' については、マニュアルを参照してください。|  
  
## 説明  
 値が指定されている場合、次のレプリケーションのストアド プロシージャでこのエラーが発生、 **@job_login** パラメーターが null または有効ではありません。 このエラーは、メンバーの場合に発生する可能性が、 **db_owner** 固定データベース ロールの以前のバージョンからのスクリプトを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではセキュリティ モデルが変更されたため、これらのスクリプトは更新する必要があります。  
  
-   [sp_addlogreader_agent & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
-   [sp_addqreader_agent & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
-   [sp_addpublication_snapshot & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
-   [sp_addpushsubscription_agent & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)  
  
-   [sp_addpullsubscription_agent & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)  
  
-   [sp_addmergepushsubscription_agent & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)  
  
-   [sp_addmergepullsubscription_agent & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)  
  
 メンバーがこれらのストアド プロシージャを実行できる、 **sysadmin** 固定サーバー ロールのメンバーか、適切なサーバーを **db_owner** 適切なデータベースの固定データベース ロール。 ストアド プロシージャはそれぞれエージェント ジョブを作成します。これにより、エージェントの実行に使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。 内のユーザーに対して、 **sysadmin** ロール、エージェント ジョブが暗黙的に作成される Windows アカウントが指定されていない場合でも (アカウントが指定されている場合) でなければ無効です。 エージェントのコンテキストで実行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 適切なサーバーでエージェント サービス アカウント。 アカウントは必要ありませんが、セキュリティ上、エージェントごとに異なるアカウントを指定することをお勧めします。 詳しくは、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
## ユーザーの操作  
 有効な Windows アカウントを指定してください、 **@job_login** 各プロシージャのパラメーターです。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からのレプリケーション スクリプトがある場合は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] に必要なストアド プロシージャやパラメーターをこれらのスクリプトに含めるように更新します。 詳細については、次を参照してください。 [レプリケーション スクリプトのアップグレード、および #40 です。レプリケーション TRANSACT-SQL プログラミングと #41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  