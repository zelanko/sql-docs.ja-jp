---
title: "外部リソース プール (TRANSACT-SQL) を削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a0aae6de75280fb0e32879ece5acea6d0fd94f3c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-external-resource-pool-transact-sql"></a>外部リソース プール (TRANSACT-SQL) を削除します。
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  外部プロセス用のリソースを定義するために使用、リソース ガバナーの外部リソース プールを削除します。 R Services 外部プールは`rterm.exe`、 `BxlServer.exe`、およびそれらにより生成された他のプロセスです。 外部リソース プールを使用して作成される[CREATE EXTERNAL RESOURCE POOL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-resource-pool-transact-sql.md)を使用して変更および[ALTER EXTERNAL RESOURCE POOL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-external-resource-pool-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
DROP EXTERNAL RESOURCE POOL pool_name  
```  
  
## <a name="arguments"></a>引数  
 *pool_name*  
 削除する外部のリソース プールの名前。  
  
## <a name="remarks"></a>解説  
 ワークロード グループが含まれている場合は、外部リソース プールを削除することはできません。  
  
 リソース ガバナーの既定のプールや内部プールを削除することはできません。  
  
 再構成が n  
  
 DDL ステートメントを実行する場合、リソース ガバナーの状態について詳しく理解しておくことをお勧めします。 詳細については、次を参照してください。[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)です。  
  
## <a name="permissions"></a>Permissions  
 必要があります`CONTROL SERVER`権限です。  
  
## <a name="examples"></a>使用例  
 次の例は、という名前の外部リソース プールを削除`ex_pool`です。  
  
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
 [外部リソース プールの変更 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [リソース プールの削除 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-resource-pool-transact-sql.md)  
  
  

