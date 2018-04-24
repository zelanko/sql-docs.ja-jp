---
title: = (代入演算子) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], assignment
- assignment operators [Transact-SQL]
- headings [SQL Server columns]
- relationships [SQL Server], assignment operators
- column headings [SQL Server]
ms.assetid: c3040db6-21d6-40ac-a783-82c98ec006cc
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5d5af73e670a2a82ebe053cc00e5f813b59d62f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="-assignment-operator-transact-sql"></a>= (代入演算子) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] の代入演算子は等号 (=) だけです。 次の例では、`@MyCounter` 変数を作成した後、代入演算子によって、`@MyCounter` を式で返される値に設定します。  
  
```  
DECLARE @MyCounter INT;  
SET @MyCounter = 1;  
```  
  
 代入演算子を使用すると、列見出しと、列の値を定義する式との関係を設定することもできます。 次の例では、列見出しの `FirstColumnHeading` と `SecondColumnHeading` を表示します。 ここでは、すべての行の `xyz` 列見出しに文字列 `FirstColumnHeading` が表示され、 続けて、`Product` テーブルの各製品 ID が `SecondColumnHeading` 列見出しに一覧表示されます。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstColumnHeading = 'xyz',  
       SecondColumnHeading = ProductID  
FROM Production.Product;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [複合演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
