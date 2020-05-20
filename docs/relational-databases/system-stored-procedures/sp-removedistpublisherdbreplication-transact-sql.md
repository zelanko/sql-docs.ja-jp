---
title: sp_removedistpublisherdbreplication (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2e169a1d8c7b68afaab973eb3f6dbb617e5bc032
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832570"
---
# <a name="sp_removedistpublisherdbreplication-transact-sql"></a>sp_removedistpublisherdbreplication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  ディストリビューター側の特定のパブリケーションに属するパブリッシュ メタデータを削除します。 このストアドプロシージャは、ディストリビューター側のディストリビューションデータベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_removedistpublisherdbreplication [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'`パブリッシャーサーバーの名前を指定します。 *publisher*は**sysname**で、既定値はありません。  
  
`[ @publisher_db = ] 'publisher_db'`パブリケーションデータベースの名前を指定します。 *publisher_db*は**sysname**で、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_removedistpublisherdbreplication**は、トランザクションレプリケーションとスナップショットレプリケーションで使用されます。  
  
 **sp_removedistpublisherdbreplication**は、ディストリビューションデータベースを削除せずにパブリッシュされたデータベースを再作成する必要がある場合に使用します。 次のメタデータが削除されます。  
  
-   すべてのパブリケーション メタデータ  
  
-   そのパブリケーションに属するすべてのアーティクルのメタデータ  
  
-   パブリケーションに対するすべてのサブスクリプションのメタデータ。  
  
-   パブリケーションに属するすべてのレプリケーションエージェントジョブのメタデータ。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_removedistpublisherdbreplication**を実行できるのは、ディストリビューター側の固定サーバーロール**sysadmin**のメンバー、またはディストリビューションデータベース内の**db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
