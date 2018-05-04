---
title: sp_helppeerrequests (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ee270d9434bea19eea08f7473dd4a6b103cb7651
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  これらの要求が実行することによって開始された、ピア ツー ピア レプリケーション トポロジ内の参加者が受信したすべての状態要求に関する情報を返します[sp_requestpeerresponse &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)いつでもトポロジでパブリッシュされたデータベースです。 このストアド プロシージャは、ピア ツー ピア レプリケーション トポロジに参加しているパブリッシャー側のパブリケーション データベースで実行されます。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication**=] **'***パブリケーション***'**  
 状態要求の送信の対象となったピア ツー ピア トポロジ内のパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ **@description**=] **'***説明***'**  
 呼び出すときに指定されている情報を定義したユーザーに基づいて返される応答をフィルター選択されるようにすること、個々 の状態要求を識別するために使用できる値[sp_requestpeerresponse &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)です。 *説明*は**nvarchar (4000)**、既定値は **%** です。 既定では、パブリケーションに対するすべての状態要求が返されます。 指定された値に一致する説明と状態要求のみを返すためにこのパラメーターを使用*説明*を使用して文字の文字列が一致するという、[と同様に&#40;TRANSACT-SQL&#41; ](../../t-sql/language-elements/like-transact-sql.md)句。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|要求を識別する値|  
|**パブリケーション**|**sysname**|状態要求の送信の対象となったパブリケーションの名前です。|  
|**sent_date**|**datetime**|状態要求が送信された日付と時刻です。|  
|**説明**|**nvarchar (4000)**|個々の状態要求を識別するために使用できるユーザー定義の情報です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helppeerrequests**はピア ツー ピア トランザクション レプリケーションで使用します。  
  
 **sp_helppeerrequests**は、ピア ツー ピア トポロジでパブリッシュされたデータベースを復元するときに使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_helppeerrequests**です。  
  
## <a name="see-also"></a>参照  
 [sp_deletepeerrequesthistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
