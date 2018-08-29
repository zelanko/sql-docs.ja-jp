---
title: sp_replshowcmds (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4572fb1e09be2064fda17860ac64beb495783177
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023431"
---
# <a name="spreplshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーション対象のマークが付けられたトランザクションのコマンドを判読可能な形式で返します。 **sp_replshowcmds**ログからレプリケートされたトランザクションを (現在の接続を含む) のクライアント接続が読んでいない場合にだけ実行できます。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>引数  
 [ **@maxtrans** =] *maxtrans*  
 情報を返すトランザクションの数です。 *maxtrans*は**int**、既定値は**1**、レプリケーションが保留中のトランザクションの最大数を指定する**sp_replshowcmds**情報を返します。  
  
## <a name="result-sets"></a>結果セット  
 **sp_replshowcmds**実行元のパブリケーション データベースに関する情報を返す診断プロシージャです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**binary(10)**|コマンドのシーケンス番号です。|  
|**originator_id**|**int**|常にコマンド オリジネータの ID **0**します。|  
|**publisher_database_id**|**int**|常にパブリッシャー データベースの ID **0**します。|  
|**article_id**|**int**|アーティクルの ID です。|  
|**type**|**int**|コマンドの種類です。|  
|**command**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] コマンド。|  
  
## <a name="remarks"></a>コメント  
 **sp_replshowcmds**はトランザクション レプリケーションで使用します。  
  
 使用して**sp_replshowcmds**、表示することは現在のトランザクションに残っているトランザクション、トランザクション ログで、ディストリビューターに送信されていない) 配布されません。  
  
 実行しているクライアント**sp_replshowcmds**と**sp_replcmds**同じデータベース内には、エラー 18752 を受け取ります。  
  
 このエラーを避けるためには、最初のクライアントを切断する必要がありますまたはログ リーダーとクライアントの役割を実行することによって解放する必要が**sp_replflush**します。 すべてのクライアントが、ログ リーダーから切断後**sp_replshowcmds**正常に実行できます。  
  
> [!NOTE]  
>  **sp_replshowcmds**レプリケーションに関する問題のトラブルシューティングにのみ実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_replshowcmds**します。  
  
## <a name="see-also"></a>参照  
 [エラー メッセージ](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
