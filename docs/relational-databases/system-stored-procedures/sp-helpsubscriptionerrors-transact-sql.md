---
title: sp_helpsubscriptionerrors (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpsubscriptionerrors_TSQL
- sp_helpsubscriptionerrors
helpviewer_keywords:
- sp_helpsubscriptionerrors
ms.assetid: 01c8bc21-939e-490d-8cc8-219c068be31e
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 87d33a74c37aaf101c9afd04a94b14939cbfb410
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpsubscriptionerrors-transact-sql"></a>sp_helpsubscriptionerrors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したサブスクリプションのすべてのトランザクション レプリケーション エラーを返します。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpsubscriptionerrors [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'   
        , [ @publication = ] 'publication'   
        , [ @subscriber = ] 'subscriber'   
        , [ @subscriber_db = ] 'subscriber_db'  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [  **@publication=** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@subscriber=** ] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値はありません。  
  
 [  **@subscriber_db=** ] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*は**sysname**、既定値はありません。  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|エラーの ID。|  
|**time**|**datetime**|エラーが発生した時刻。|  
|**error_type_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**source_type_id**|**int**|エラー ソース タイプ ID。|  
|**source_name**|**nvarchar(100)**|エラー ソースの名前。|  
|**error_code**|**sysname**|エラー コードです。|  
|**error_text**|**ntext**|エラー メッセージ。|  
|**xact_seqno**|**varbinary(16)**|失敗した実行バッチの先頭のトランザクション ログ シーケンス番号。 これは、ディストリビューション エージェントでのみ使用されます。失敗した実行バッチ内にある、先頭のトランザクションのトランザクション ログ シーケンス番号です。|  
|**command_id**|**int**|失敗した実行バッチのコマンド ID。 これは、ディストリビューション エージェントでのみ使用されます。失敗した実行バッチ内にある、先頭のコマンドのコマンド ID です。|  
|**session_id**|**int**|エラーが発生したエージェント セッションの ID。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpsubscriptionerrors**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_helpsubscriptionerrors**です。  
  
## <a name="see-also"></a>参照  
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
