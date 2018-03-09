---
title: "sp_reinitmergesubscription (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_reinitmergesubscription_TSQL
- sp_reinitmergesubscription
helpviewer_keywords:
- sp_reinitmergesubscription
ms.assetid: 249a4048-e885-48e0-a92a-6577f59de751
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b801376850844a0e1cba0e5b53b72114c0199f7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spreinitmergesubscription-transact-sql"></a>sp_reinitmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ エージェントの次回実行時に再初期化するように、マージ サブスクリプションにマークを付けます。 このストアド プロシージャは、パブリッシャーのパブリケーション データベースで実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_reinitmergesubscription [ [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber'  
    [ , [ @subscriber_db = ] 'subscriber_db'  
    [ , [ @upload_first = ] 'upload_first'  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication =** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は**すべて**です。  
  
 [  **@subscriber =** ] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は**すべて**です。  
  
 [  **@subscriber_db =** ] **'***@subscriber_db***'**  
 サブスクライバー データベースの名前です。 *@subscriber_db*は**sysname**、既定値は**すべて**です。  
  
 [  **@upload_first =** ] **'***@upload_first***'**  
 サブスクリプションを再初期化する前にサブスクライバーの変更をアップロードするかどうかを指定します。 *@upload_first*は**nvarchar (5)**、既定値は FALSE。 場合**true**サブスクリプションを再初期化する前に変更がアップロードされます。 場合**false**変更はアップロードされません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_reinitmergesubscription**はマージ レプリケーションで使用します。  
  
 **sp_reinitmergesubscription**マージ サブスクリプションを再初期化に、パブリッシャーから呼び出すことができます。 その際には、スナップショット エージェントも再実行することをお勧めします。  
  
 パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_reinitmergepushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_1.sql)]  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_reinitmergepushsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_2.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_reinitmergesubscription**です。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
