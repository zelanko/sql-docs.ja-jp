---
title: DROP EXTERNAL RESOURCE POOL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL RESOURCE POOL
- DROP_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL RESOURCE POOL statement
ms.assetid: e2fa01bd-96ff-4ea9-bb08-6cb6b6adf68c
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b31fb10c0de6d439b20713ec4e7684ea5b9d98e4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="drop-external-resource-pool-transact-sql"></a>DROP EXTERNAL RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  外部プロセス用のリソースの定義に使われる Resource Governor 外部リソース プールを削除します。 R Services の場合、外部プールは `rterm.exe`、 `BxlServer.exe` およびそれらにより生成された他のプロセスを制御します。 外部リソース プールの作成には [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md) を使い、変更には [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md) を使います。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>構文  
  
```  
DROP EXTERNAL RESOURCE POOL pool_name  
```  
  
## <a name="arguments"></a>引数  
 *pool_name*  
 削除する外部リソース プールの名前。  
  
## <a name="remarks"></a>Remarks  
 ワークロード グループが含まれている場合は、外部リソース プールを削除できません。  
  
 リソース ガバナーの既定のプールや内部プールを削除することはできません。  
  
 再構成は  
  
 DDL ステートメントを実行する場合、リソース ガバナーの状態について詳しく理解しておくことをお勧めします。 詳細については、「[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 `CONTROL SERVER` 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`ex_pool` という外部リソース プールを削除します。  
  
```  
DROP EXTERNAL RESOURCE POOL ex_pool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [SQL Server R Services の既知の問題](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)  
  
  
