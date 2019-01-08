---
title: sp_removedistpublisherdbreplication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_removedistpublisherdbreplication_TSQL
- sp_removedistpublisherdbreplication
helpviewer_keywords:
- sp_removedistpublisherdbreplication
ms.assetid: 9bfe002a-25b5-4226-bcfb-feb2060d6b4a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d57034b65559e696a9692a1c71e612c7d921661b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52754644"
---
# <a name="spremovedistpublisherdbreplication-transact-sql"></a>sp_removedistpublisherdbreplication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューター側の特定のパブリケーションに属するパブリッシュ メタデータを削除します。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_removedistpublisherdbreplication [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 パブリッシャー サーバーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_removedistpublisherdbreplication**トランザクションとスナップショット レプリケーションで使用されます。  
  
 **sp_removedistpublisherdbreplication**もディストリビューション データベースを削除しない限り、パブリッシュされたデータベースを再作成する必要があるときに使用されます。 次のメタデータが削除されます。  
  
-   すべてのパブリケーション メタデータ  
  
-   そのパブリケーションに属するすべてのアーティクルのメタデータ  
  
-   そのパブリケーションのすべてのサブスクリプションのメタデータ  
  
-   そのパブリケーションに属するすべてのレプリケーション エージェント ジョブのメタデータ  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**のメンバー、またはディストリビューターの固定サーバー ロール、 **db_owner**ディストリビューション データベースの固定データベース ロールが実行できる**sp _removedistpublisherdbreplication**します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
