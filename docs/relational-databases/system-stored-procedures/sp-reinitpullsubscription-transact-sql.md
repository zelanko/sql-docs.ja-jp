---
title: sp_reinitpullsubscription (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
- sp_reinitpullsubscription_TSQL
- sp_reinitpullsubscription
helpviewer_keywords:
- sp_reinitpullsubscription
ms.assetid: 7d9abe49-ce92-47f3-82c9-aea749518c91
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ab14d01f4d77d249b0d2ff74afd2e6c08668c18e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spreinitpullsubscription-transact-sql"></a>sp_reinitpullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューション エージェントの次回実行時に再初期化するように、トランザクション プル サブスクリプションまたは匿名サブスクリプションにマークを付けます。 このストアド プロシージャは、サブスクライバー側でプル サブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_reinitpullsubscription [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、すべての既定値は、再初期化のすべてのサブスクリプションを設定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_reinitpullsubscription**トランザクション レプリケーションで使用します。  
  
 **sp_reinitpullsubscription**ピア ツー ピア トランザクション レプリケーションはサポートされていません。  
  
 **sp_reinitpullsubscription**ディストリビューション エージェントの次回実行時に、サブスクリプションを再初期化するサブスクライバーから呼び出すことができます。  
  
 値で作成されたパブリケーションに対するサブスクリプション**false**の**@immediate_sync**サブスクライバーから再初期化することはできません。  
  
 いずれかを実行してプル サブスクリプションを再初期化することができます**sp_reinitpullsubscription**サブスクライバーまたは**sp_reinitsubscription**パブリッシャー側でします。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_reinitpullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitpullsubscriptio_1.sql)]  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_reinitpullsubscription**です。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
