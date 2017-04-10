---
title: "MSSQL_ENG021798 | Microsoft Docs"
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
  - "MSSQL_ENG021798 エラー"
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG021798
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21798|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|続行する前に、'%s' エージェント ジョブを '%s' から追加してください。 '%s' については、マニュアルを参照してください。|  
  
## 説明  
 パブリケーションを作成する、 **sysadmin** のメンバーか、パブリッシャー側の固定サーバー ロール、 **db_owner** パブリケーション データベースの固定データベース ロール。 メンバーである場合、 **db_owner** ロールでは、このエラーが発生する場合。  
  
-   [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] からスクリプトを実行する場合。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではセキュリティ モデルが変更されたため、これらのスクリプトは更新する必要があります。  
  
-   ストアド プロシージャ **sp_addpublication** が実行する前に実行される [sp_addlogreader_agent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)します。 これはすべてのトランザクション パブリケーションに当てはまります。  
  
-   ストアド プロシージャ **sp_addpublication** が実行する前に実行される [sp_addqreader_agent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)します。 これは、キュー更新サブスクリプションが有効になっているトランザクション パブリケーションに適用されます (値の TRUE の場合、 **@allow_queued_tran** のパラメーター **sp_addpublication**)。  
  
 ストアド プロシージャ **sp_addlogreader_agent** と **sp_addqreader_agent** エージェント ジョブを作成して指定すること、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] エージェントを実行する Windows アカウントです。 内のユーザーに対して、 **sysadmin** ロール、エージェント ジョブが暗黙的に作成される場合は **sp_addlogreader_agent** と **sp_addqreader_agent** は実行されません。 エージェントのコンテキストで実行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターでエージェント サービス アカウント。  **Sp_addlogreader_agent** と **sp_addqreader_agent** 内のユーザーには必要ありません、 **sysadmin** ロール、エージェントを別のアカウントを指定するセキュリティのベスト プラクティスであります。 詳しくは、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
## ユーザーの操作  
 正しい順序でプロシージャを実行してください。 詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からのレプリケーション スクリプトがある場合は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンに必要なストアド プロシージャおよびパラメーターをこれらのスクリプトに含めるように更新します。 詳細については、次を参照してください。 [レプリケーション スクリプトのアップグレード、および #40 です。レプリケーション TRANSACT-SQL プログラミングと #41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)です。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  