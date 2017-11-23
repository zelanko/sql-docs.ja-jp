---
title: "sp_configure_peerconflictdetection (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_configure_peerconflictdetection_TSQL
- sp_configure_peerconflictdetection
helpviewer_keywords: sp_configure_peerconflictdetection
ms.assetid: 45117cb2-3247-433f-ba3d-7fa19514b1c3
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1fed4cb47795554df26deb08f496edba86b5a4d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spconfigurepeerconflictdetection-transact-sql"></a>sp_configure_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ピア ツー ピア トランザクション レプリケーション トポロジに関係するパブリケーションの競合検出を構成します。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_configure_peerconflictdetection [ @publication = ] 'publication'  
    [ , [ @action = ] 'action']  
    [ , [ @originator_id = ] originator_id ]  
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @continue_onconflict = ] 'continue_onconflict']  
    [ , [ @local = ] 'local']  
    [ , [ @timeout = ] timeout ]  
  
```  
  
## <a name="arguments"></a>引数  
 [ @publication=] '*パブリケーション*'  
 競合検出を構成するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ @action=] '*アクション*'  
 パブリケーションの競合検出を有効にするか無効にするかを指定します。 *アクション*は**nvarchar (5)**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**有効にします。**|パブリケーションの競合検出を有効にします。|  
|**無効にします。**|パブリケーションの競合検出を無効にします。|  
|NULL (既定値)||  
  
 [ @originator_id=] *originator_id*  
 ピア ツー ピア トポロジ内のノードの ID を指定します。 *originator_id*は**int**、既定値は NULL です。 場合、この ID は競合検出に対して使用*アクション*に設定されている**を有効にする**です。 トポロジで使用されていないゼロ以外の正の ID を指定してください。 既に使用されている ID を確認するには、 [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) システム テーブルに対してクエリを実行します。  
  
 [ @conflict_retention=] *conflict_retention*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @continue_onconflict=] '*continue_onconflict*']  
 競合の検出後にディストリビューション エージェントで変更の処理を続行するかどうかを示します。 *continue_onconflict*は**nvarchar (5)**で既定値は FALSE。  
  
> [!CAUTION]  
>  既定値の FALSE を使用することをお勧めします。 このオプションを TRUE に設定すると、ディストリビューション エージェントは、発信元 ID が最も大きいノードから競合する行を適用してトポロジ内のデータを収束しようとします。 この方法では収束が保証されません。 競合が検出された後に、トポロジに一貫性があることを確認する必要があります。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」の「競合の処理」を参照してください。  
  
 [ @local=] '*ローカル*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @timeout=]*タイムアウト*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_configure_peerconflictdetection は、ピア ツー ピア トランザクション レプリケーションで使用されます。 競合の検出を使用するのには、すべてのノードを実行する必要がある[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]かすべてのノードで、以降のバージョンと検出が有効にする必要があります。  
  
## <a name="permissions"></a>Permissions  
 固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ピア ツー ピア レプリケーションにおける競合検出](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
