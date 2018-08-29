---
title: sp_helpreplfailovermode (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- sp_helpreplfailovermode
- sp_helpreplfailovermode_TSQL
helpviewer_keywords:
- sp_helpreplfailovermode
ms.assetid: d1090e42-6840-4bf6-9aa9-327fd8987ec2
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b350ac28a53dbdb544f3dde0b3493cd40436bca3
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031364"
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
 [ **@publisher=**] **'***publisher***'**  
 サブスクライバーの更新に関係しているパブリッシャーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。 パブリッシャーは、パブリッシング用にあらかじめ構成されている必要があります。  
  
 [  **@publisher_db =**] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication=**] **'***publication***'**  
 サブスクライバーの更新に関係しているパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@failover_mode_id=**] **'***failover_mode_id***' 出力**  
 フェールオーバー モードの整数値を返し、、**出力**パラメーター。 *failover_mode_id*は、 **tinyint** 、既定値は**0**します。 返します**0**即時更新と**1**のキュー更新します。  
  
 [**@failover_mode=**] **'***failover_mode***' 出力**  
 サブスクライバーでデータ変更が行われるモードを返します。 *failover_mode*は、 **nvarchar (10)** 既定値は NULL です。 **出力**パラメーター。  
  
|値|説明|  
|-----------|-----------------|  
|**イミディ エイト**|即時更新。サブスクライバーでの更新は、2 フェーズ コミット プロトコル (2PC) を使ってパブリッシャーに即座に通知されます。|  
|**キューに登録**|キュー更新。サブスクライバーでの更新は、キューに格納されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpreplfailovermode**更新エラーが発生した場合、フェールオーバーとしてキューを使用する即時更新サブスクリプションが有効になっているは、スナップショット レプリケーションまたはトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_helpreplfailovermode**します。  
  
## <a name="see-also"></a>参照  
 [sp_setreplfailovermode &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
