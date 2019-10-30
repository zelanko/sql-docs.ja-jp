---
title: sp_helpreplfailovermode (Transact-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplfailovermode
- sp_helpreplfailovermode_TSQL
helpviewer_keywords:
- sp_helpreplfailovermode
ms.assetid: d1090e42-6840-4bf6-9aa9-327fd8987ec2
author: stevestein
ms.author: sstein
ms.openlocfilehash: ff5bd9978be59f6a512ce4173b851692b9506d96
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997556"
---
# <a name="sphelpreplfailovermode-transact-sql"></a>sp_helpreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクリプションの現在のフェールオーバー モードを表示します。 このストアド プロシージャは、任意のデータベース上のサブスクライバー側で実行されます。 フェールオーバー モードの詳細については、次を参照してください。[更新可能な Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpreplfailovermode [ @publisher= ] 'publisher'   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]   
    [ , [ @failover_mode_id= ] 'failover_mode_id'OUTPUT]   
    [ , [ @failover_mode = ] 'failover_mode'OUTPUT]   
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` このサブスクライバーの更新プログラムに参加しているパブリッシャーの名前です。 *パブリッシャー* は **sysname** 、既定値はありません。 パブリッシャーは、発行のため構成されている必要があります。  
  
`[ @publisher_db = ] 'publisher_db'` パブリケーション データベースの名前です。 *publisher_db* は **sysname** 、既定値はありません。  
  
`[ @publication = ] 'publication'` このサブスクライバーの更新プログラムに参加しているパブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
`[ @failover_mode_id = ] 'failover_mode_id' OUTPUT` フェールオーバー モードの整数値を返し、、**出力**パラメーター。 *failover_mode_id*は、 **tinyint** 、既定値は**0**します。 返します**0**即時更新と**1**のキュー更新します。  
  
 [**\@failover_mode=**] **'***failover_mode***' 出力**  
 サブスクライバーでデータ変更が行われるモードを返します。 *failover_mode*は、 **nvarchar (10)** 既定値は NULL です。 **出力**パラメーター。  
  
|値|説明|  
|-----------|-----------------|  
|**immediate**|即時更新します。 サブスクライバーで更新プログラムはすぐに 2 フェーズ コミット プロトコル (2 pc) を使用してパブリッシャーに反映されます。|  
|**queued**|キュー更新。サブスクライバーでの更新は、キューに格納されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpreplfailovermode**更新エラーが発生した場合、フェールオーバーとしてキューを使用する即時更新サブスクリプションが有効になっているは、スナップショット レプリケーションまたはトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_helpreplfailovermode**します。  
  
## <a name="see-also"></a>参照  
 [sp_setreplfailovermode &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
