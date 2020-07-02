---
title: sp_setreplfailovermode (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fc6851a9467f0d3f9e3a9becb2f3e3aa6fdb88c3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85645284"
---
# <a name="sp_setreplfailovermode-transact-sql"></a>sp_setreplfailovermode (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  フェールオーバーとしてキュー更新を使用する即時更新が有効になっているサブスクリプションに対して、フェールオーバー操作モードを設定できます。 このストアドプロシージャは、サブスクライバー側のサブスクリプションデータベースで実行されます。 フェールオーバーモードの詳細については、「[トランザクションレプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_setreplfailovermode [ @publisher= ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication= ] 'publication' ]  
    [ , [ @failover_mode= ] 'failover_mode' ]  
    [ , [ @override = ] override ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'`パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。 パブリケーションは既に存在している必要があります。  
  
`[ @publisher_db = ] 'publisher_db'`パブリケーションデータベースの名前を指定します。 *publisher_db*は**sysname**であり、既定値はありません。  
  
`[ @publication = ] 'publication'`パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @failover_mode = ] 'failover_mode'`は、サブスクリプションのフェールオーバーモードです。 *failover_mode*は**nvarchar (10)** で、次のいずれかの値を指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**イミディエイト**または**同期**|サブスクライバーで行われたデータ変更は、変更の発生時にパブリッシャーに一括コピーされます。|  
|**queued**|データの変更はキューに格納され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージキューは非推奨とされており、サポートされなくなりました。  
  
`[ @override = ] override`内部でのみ使用します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_setreplfailovermode**は、サブスクリプションが有効になっているスナップショットレプリケーションまたはトランザクションレプリケーションで、即時更新へのフェールオーバーを伴うキュー更新、または即時更新 (キュー更新を使用した即時更新) のいずれかに使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_setreplfailovermode**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [更新可能なトランザクションサブスクリプションの更新モードを切り替える](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
