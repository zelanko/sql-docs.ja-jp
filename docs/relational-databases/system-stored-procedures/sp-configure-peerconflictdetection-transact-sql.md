---
title: sp_configure_peerconflictdetection (TRANSACT-SQL) |Microsoft Docs
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
- sp_configure_peerconflictdetection_TSQL
- sp_configure_peerconflictdetection
helpviewer_keywords:
- sp_configure_peerconflictdetection
ms.assetid: 45117cb2-3247-433f-ba3d-7fa19514b1c3
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07555d1f5e26538b1bdf980c65d5f08cfa546717
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031659"
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
 [ @publication=] '*publication*'  
 競合検出を構成するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ @action=] '*アクション*'  
 パブリケーションの競合検出を有効にするか無効にするかを指定します。 *アクション*は**nvarchar (5)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**enable**|パブリケーションの競合検出を有効にします。|  
|**disable**|パブリケーションの競合検出を無効にします。|  
|NULL (既定値)||  
  
 [ @originator_id= ] *originator_id*  
 ピア ツー ピア トポロジ内のノードの ID を指定します。 *originator_id*は**int**、既定値は NULL です。 場合、この ID は競合検出に対して使用*アクション*に設定されている**を有効にする**します。 トポロジで使用されていないゼロ以外の正の ID を指定してください。 既に使用されている ID を確認するには、 [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) システム テーブルに対してクエリを実行します。  
  
 [ @conflict_retention= ] *conflict_retention*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @continue_onconflict= ] '*continue_onconflict*' ]  
 競合の検出後にディストリビューション エージェントで変更の処理を続行するかどうかを示します。 *continue_onconflict*は**nvarchar (5)** で既定値は FALSE。  
  
> [!CAUTION]  
>  既定値の FALSE を使用することをお勧めします。 このオプションを TRUE に設定すると、ディストリビューション エージェントは、発信元 ID が最も大きいノードから競合する行を適用してトポロジ内のデータを収束しようとします。 この方法では収束が保証されません。 競合が検出された後に、トポロジに一貫性があることを確認する必要があります。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」の「競合の処理」を参照してください。  
  
 [ @local= ] '*local*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @timeout= ] *timeout*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 sp_configure_peerconflictdetection は、ピア ツー ピア トランザクション レプリケーションで使用されます。 競合の検出を使用するすべてのノードを実行する必要があります[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]またはすべてのノードは、以降のバージョンと検出を有効にする必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ピア ツー ピア レプリケーションにおける競合検出](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
