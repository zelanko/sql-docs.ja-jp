---
title: "DROP SYNONYM (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 25af262ddc5655bc42e4893daecefe0cd8fb85d9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定されたスキーマからシノニムを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 条件付きでは既に存在する場合にのみ、シノニムを削除します。  
  
 *スキーマ*  
 シノニムが存在するスキーマを指定します。 スキーマが指定されていない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]現在のユーザーの既定のスキーマを使用します。  
  
 *synonym_name*  
 削除するシノニムの名前です。  
  
## <a name="remarks"></a>解説  
 シノニムへの参照はスキーマにバインドされていません。したがってシノニムはいつでも削除できます。 削除したシノニムへの参照は、実行時にのみ検出されます。  
  
 シノニムは、動的な SQL で作成、削除、および参照できます。  
  
## <a name="permissions"></a>Permissions  
 シノニムを削除するには、ユーザーは次の条件を少なくとも 1 つ 満たしている必要があります。  
  
-   シノニムの現在の所有者である。  
  
-   シノニムに対する CONTROL を許可されている。  
  
-   シノニムを含むスキーマに対する ALTER SCHEMA 権限を許可されている。  
  
## <a name="examples"></a>使用例  
 次の例では、シノニム、まずを作成`MyProduct`、し、シノニムを削除します。  
  
```  
USE tempdb;  
GO  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
-- Drop synonym MyProduct.  
USE tempdb;  
GO  
DROP SYNONYM MyProduct;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [シノニム &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
