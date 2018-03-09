---
title: "DROP ROUTE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ROUTE
- DROP_ROUTE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping routes
- DROP ROUTE statement
- deleting routes
- routes [Service Broker], removing
- removing routes
ms.assetid: d8fab0bc-d54a-46ca-9437-552db7477d40
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f63dbf4868d0b1add92d0971a11eaab0fb7a6629
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="drop-route-transact-sql"></a>DROP ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ルートを削除し、その情報を現在のデータベースのルーティング テーブルから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP ROUTE route_name  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *route_name*  
 削除するルートの名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
## <a name="remarks"></a>解説  
 ルートを格納するルーティング テーブルは、カタログ ビューを介して読み取ることができるメタデータ テーブル**sys.routes**です。 このルーティング テーブルは、CREATE ROUTE、ALTER ROUTE、および DROP ROUTE ステートメントでのみ更新できます。  
  
 メッセージ交換でルートが使用されているかどうかに関係なく、ルートを削除することができますが、 リモート サービスへのルートが他に存在しない場合は、リモート サービスへのルートが作成されるか、メッセージ交換がタイムアウトになるまで、メッセージ交換のメッセージは転送キューに残ります。  
  
## <a name="permissions"></a>権限  
 ルートを削除する権限は、既定ではルートの所有者、db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
 次の例では、`ExpenseRoute` ルートを削除します。  
  
```  
DROP ROUTE ExpenseRoute ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER ROUTE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-route-transact-sql.md)   
 [CREATE ROUTE &#40;Transact-SQL&#41;](../../t-sql/statements/create-route-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.routes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-routes-transact-sql.md)  
  
  
