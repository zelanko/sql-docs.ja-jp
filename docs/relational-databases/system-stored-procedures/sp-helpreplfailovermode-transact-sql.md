---
title: "sp_helpreplfailovermode (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_helpreplfailovermode
- sp_helpreplfailovermode_TSQL
helpviewer_keywords: sp_helpreplfailovermode
ms.assetid: d1090e42-6840-4bf6-9aa9-327fd8987ec2
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 212775844dde7400ca3ddb17753091aa56b582f1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpreplfailovermode-transact-sql"></a>sp_helpreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクリプションの現在のフェールオーバー モードを表示します。 このストアド プロシージャは、任意のデータベース上のサブスクライバー側で実行されます。 フェールオーバー モードの詳細については、次を参照してください。[トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)です。  
  
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
 [  **@publisher=**] **'***パブリッシャー***'**  
 サブスクライバーの更新に関係しているパブリッシャーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。 パブリッシャーは、パブリッシング用にあらかじめ構成されている必要があります。  
  
 [  **@publisher_db =**] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [  **@publication=**] **'***パブリケーション***'**  
 サブスクライバーの更新に関係しているパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@failover_mode_id=**] **'***failover_mode_id***' 出力**  
 フェールオーバー モードの整数値を返し、、**出力**パラメーター。 *failover_mode_id*は、 **tinyint** 、既定値は**0**します。 返します**0**即時更新および**1**キュー更新します。  
  
 [**@failover_mode=**] **'***failover_mode***' 出力**  
 サブスクライバーでデータ変更が行われるモードを返します。 *failover_mode*は、 **nvarchar (10)**既定値は NULL です。 **出力**パラメーター。  
  
|値|Description|  
|-----------|-----------------|  
|**イミディ エイト**|即時更新。サブスクライバーでの更新は、2 フェーズ コミット プロトコル (2PC) を使ってパブリッシャーに即座に通知されます。|  
|**キューに置かれました。**|キュー更新。サブスクライバーでの更新は、キューに格納されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpreplfailovermode**で即時更新サブスクリプションが有効になっているフェールオーバーとしてキュー更新、障害発生時に、スナップショット レプリケーションまたはトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_helpreplfailovermode**です。  
  
## <a name="see-also"></a>参照  
 [sp_setreplfailovermode &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
