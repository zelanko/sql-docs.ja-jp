---
title: sp_helpmergealternatepublisher (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- sp_helpmergealternatepublisher_TSQL
- sp_helpmergealternatepublisher
helpviewer_keywords:
- sp_helpmergealternatepublisher
ms.assetid: a96e365f-5967-4580-9d79-5bacf2d12211
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9a66e9c0343a4441d3a5bf370d96ff7f6bf61370
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpmergealternatepublisher-transact-sql"></a>sp_helpmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションの代替パブリッシャーとして有効なすべてのサーバーの一覧を返します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergealternatepublisher [ @publisher = ] 'publisher', [ @publisher_db = ] 'publisher_db', [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher=**] **'***publisher***'**  
 代替パブリッシャーの名前です。*パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリケーション データベースの名前です。*publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。*パブリケーション*は**sysname**、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**alternate_publisher**|**sysname**|代替パブリッシャーの名前です。|  
|**alternate_publisher_db**|**sysname**|パブリケーション データベースの名前です。|  
|**alternate_publication**|**sysname**|パブリケーションの名前です。|  
|**alternate_distributor**|**sysname**|ディストリビューターの名前。|  
|**friendly_name**|**nvarchar (255)**|代替パブリッシャーの説明。|  
|**enabled**|**bit**|サーバーが代替パブリッシャーかどうかを示します。 **1**パブリッシャーが代替パブリッシャーとして有効になっているを指定します。 **0**は無効になっているを指定します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergealternatepublisher**はマージ レプリケーションで使用します。  
  
 マージ セッションごとに、システムではパブリッシャーとサブスクライバーの両方に対し、代替パブリッシャーの一覧を求めるクエリが実行されます。 マージ処理では代替パブリッシャーの一覧に対してエントリの追加や削除が行われ、サブスクライバーとパブリッシャーの両方に一致する代替パブリッシャーの一覧が生成されます。  
  
## <a name="permissions"></a>権限  
 パブリケーションのパブリケーション アクセス リストのメンバーだけが実行できる**sp_helpmergealternatepublisher**です。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
