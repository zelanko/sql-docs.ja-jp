---
title: "SET NOCOUNT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NOCOUNT
- SET_NOCOUNT_TSQL
- NOCOUNT_TSQL
- SET NOCOUNT
dev_langs:
- TSQL
helpviewer_keywords:
- NOCOUNT option
- number of rows affected by statement
- row affected by statements [SQL Server]
- counting rows
- SET NOCOUNT statement
ms.assetid: eb3e6727-cb26-4bc2-84c7-171cbac02029
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5e8224b906de8f8678a33360be6222aa2120a5b8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-nocount-transact-sql"></a>SET NOCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  影響を受ける行の数の数を示すメッセージを停止する、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはストアド プロシージャ、結果の一部として返されるを設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET NOCOUNT { ON | OFF }   
```  
  
## <a name="remarks"></a>解説  
 SET NOCOUNT が ON の場合、行数は返されません。 SET NOCOUNT が OFF の場合、行数が返されます。  
  
 @@ROWCOUNT SET NOCOUNT が ON の場合でも、関数が更新されました。  
  
 SET NOCOUNT ON を指定すると、ストアド プロシージャ内の各ステートメントに対する DONE_IN_PROC メッセージは、クライアントに送信されなくなります。 多くの実際のデータを返さないいくつかのステートメントを含んでいるストアド プロシージャまたはを含むプロシージャの[!INCLUDE[tsql](../../includes/tsql-md.md)]ネットワーク トラフィックが大幅に縮小されるため、ループで、大幅なパフォーマンスを向上させることができます提供 SET NOCOUNT を ON に設定します。  
  
 SET NOCOUNT で指定される設定は、解析時ではなく実行時に有効になります。  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @NOCOUNT VARCHAR(3) = 'OFF';  
IF ( (512 & @@OPTIONS) = 512 ) SET @NOCOUNT = 'ON';  
SELECT @NOCOUNT AS NOCOUNT;  
  
```  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、処理された行数に関するメッセージを表示しないようにします。  
  
```  
USE AdventureWorks2012;  
GO  
SET NOCOUNT OFF;  
GO  
-- Display the count message.  
SELECT TOP(5)LastName  
FROM Person.Person  
WHERE LastName LIKE 'A%';  
GO  
-- SET NOCOUNT to ON to no longer display the count message.  
SET NOCOUNT ON;  
GO  
SELECT TOP(5) LastName  
FROM Person.Person  
WHERE LastName LIKE 'A%';  
GO  
-- Reset SET NOCOUNT to OFF  
SET NOCOUNT OFF;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

