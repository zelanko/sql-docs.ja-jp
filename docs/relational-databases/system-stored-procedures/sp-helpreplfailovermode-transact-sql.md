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
ms.openlocfilehash: 5b9c8322507c78458110f47f579ec333c3e5e7a7
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73142846"
---
# <a name="sp_helpreplfailovermode-transact-sql"></a>sp_helpreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクリプションの現在のフェールオーバー モードを表示します。 このストアド プロシージャは、任意のデータベース上のサブスクライバー側で実行されます。 フェールオーバーモードの詳細については、「[トランザクションレプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpreplfailovermode [ @publisher= ] 'publisher'   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]   
    [ , [ @failover_mode_id= ] 'failover_mode_id'OUTPUT]   
    [ , [ @failover_mode = ] 'failover_mode'OUTPUT]   
```  
  
## <a name="arguments"></a>[引数]  
`[ @publisher = ] 'publisher'` は、このサブスクライバーの更新に参加しているパブリッシャーの名前です。 *publisher*は**sysname**で、既定値はありません。 パブリッシャーは、既に発行用に構成されている必要があります。  
  
`[ @publisher_db = ] 'publisher_db'` は、パブリケーションデータベースの名前です。 *publisher_db*は**sysname**,、既定値はありません。  
  
`[ @publication = ] 'publication'` は、このサブスクライバーの更新に参加しているパブリケーションの名前です。 *publication*は**sysname**,、既定値はありません。  
  
`[ @failover_mode_id = ] 'failover_mode_id' OUTPUT` は、フェールオーバーモードの整数値を返し、は**出力**パラメーターです。 *failover_mode_id*は**tinyint**で、既定値は**0**です。 即時更新の場合は**0** 、キュー更新の場合は**1**を返します。  
  
 [ **\@failover_mode =** ] **'***failover_mode***' 出力**  
 サブスクライバーでデータ変更が行われるモードを返します。 *failover_mode*は**nvarchar (10)** で、既定値は NULL です。 は**出力**パラメーターです。  
  
|の値|Description|  
|-----------|-----------------|  
|**immediate**|即時更新: サブスクライバーで行われた更新は、2 フェーズ コミット プロトコル (2PC) を使用してパブリッシャーに直ちに反映されます。|  
|**queued**|キュー更新。サブスクライバーでの更新は、キューに格納されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>備考  
 **sp_helpreplfailovermode**は、失敗した場合に、フェールオーバーとしてキュー更新を使用する即時更新が有効になっているスナップショットレプリケーションまたはトランザクションレプリケーションで使用されます。  
  
## <a name="permissions"></a>Permissions  
 **Sp_helpreplfailovermode**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>「  
 [sp_setreplfailovermode &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
