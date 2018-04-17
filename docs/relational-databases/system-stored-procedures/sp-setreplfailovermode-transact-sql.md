---
title: sp_setreplfailovermode (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39e640d539dad66402d90fc450b5c22a1e338f89
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spsetreplfailovermode-transact-sql"></a>sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクリプションが、フェールオーバーとしてキュー更新を使用する即時更新に対して有効になっている場合、このサブスクリプションのフェールオーバー操作モードを設定できます。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。 フェールオーバー モードの詳細については、次を参照してください。[トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)です。  
  
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
 [ **@publisher=**] **'***publisher***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。 パブリケーションは既に存在している必要があります。  
  
 [  **@publisher_db =**] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [**@failover_mode=**] **'***failover_mode***'**  
 サブスクリプションのフェールオーバー モードを指定します。 *failover_mode*は**nvarchar (10)**これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**イミディ エイト**または**同期**|サブスクライバーで行われたデータ変更は、変更の発生時にパブリッシャーに一括コピーされます。|  
|**キューに置かれました。**|データ変更は、格納、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キュー。|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] メッセージ キューは廃止されており、現在サポートされていません。  
  
 [ **@override**=]*オーバーライド*  
 内部使用のみです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_setreplfailovermode**はスナップショット レプリケーションまたはトランザクション レプリケーションでのサブスクリプションを有効にするか、キュー更新を即時更新にフェールオーバーを伴うまたは使用フェールオーバーを伴う即時更新キューに登録するには更新しています。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_setreplfailovermode**です。  
  
## <a name="see-also"></a>参照  
 [更新可能トランザクション サブスクリプションの更新モードを切り替える](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
