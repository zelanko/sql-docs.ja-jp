---
title: MSSQL_ENG021798 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 51cf4acc8ed270c8302137fe5050c06cb35e91ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63023530"
---
# <a name="mssql_eng021798"></a>MSSQL_ENG021798
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21798|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|続行する前に、'%s' エージェント ジョブを '%s' から追加してください。 '%s' については、マニュアルを参照してください。|  
  
## <a name="explanation"></a>説明  
 パブリケーションを作成するには、パブリッシャーの **sysadmin** 固定サーバー ロールのメンバーまたはパブリケーション データベースの **db_owner** 固定データベース ロールのメンバーであることが必要です。 **db_owner** ロールのメンバーのときは、以下の場合にこのエラーが発生します。  
  
-   [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]からスクリプトを実行する場合。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ではセキュリティ モデルが変更されたため、これらのスクリプトは更新する必要があります。  
  
-   **sp_addlogreader_agent &#40;Transact-SQL&#41;** を実行する前に、ストアド プロシージャ [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) が実行される場合。 これはすべてのトランザクション パブリケーションに当てはまります。  
  
-   **sp_addqreader_agent &#40;Transact-SQL&#41;** を実行する前に、ストアド プロシージャ [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) が実行される場合。 これは、キュー更新サブスクリプションに対して有効になっているトランザクションパブリケーションに適用さ**@allow_queued_tran**れます ( **sp_addpublication**のパラメーターの値は TRUE です)。  
  
 ストアド プロシージャ **sp_addlogreader_agent** および **sp_addqreader_agent** は、それぞれエージェント ジョブを作成します。これにより、エージェントの実行に使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。 **sp_addlogreader_agent** および **sp_addqreader_agent** が実行されていない場合は、 **sysadmin** ロールのユーザーに対し、エージェント ジョブが暗黙的に作成されます。エージェントは、ディストリビューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントのコンテキストで実行されます。 **sysadmin** ロールでは、ユーザーは **sp_addlogreader_agent** および **sp_addqreader_agent** を必要としませんが、セキュリティ上、エージェントごとに異なるアカウントを指定することをお勧めします。 詳細については、「 [レプリケーション エージェント セキュリティ モデル](security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
 正しい順序でプロシージャを実行してください。 詳細については、「[パブリケーションの作成](publish/create-a-publication.md)」を参照してください。以降のバージョンで[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]必要なストアドプロシージャおよびパラメーターを含めるように、これらのスクリプトを更新してください。 詳細については、「[レプリケーション スクリプトのアップグレード &#40;レプリケーション Transact-SQL プログラミング&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  
