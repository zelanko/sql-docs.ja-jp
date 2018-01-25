---
title: "= (代入演算子) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- operators [Transact-SQL], assignment
- assignment operators [Transact-SQL]
- headings [SQL Server columns]
- relationships [SQL Server], assignment operators
- column headings [SQL Server]
ms.assetid: c3040db6-21d6-40ac-a783-82c98ec006cc
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c21e0e9525a68c423cbf273d3a5a8ba3aa3da04a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="-assignment-operator-transact-sql"></a>= (代入演算子) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] の代入演算子は等号 (=) だけです。 次の例では、`@MyCounter` 変数を作成した後、代入演算子によって、`@MyCounter` を式で返される値に設定します。  
  
```  
DECLARE @MyCounter INT;  
SET @MyCounter = 1;  
```  
  
 代入演算子を使用すると、列見出しと、列の値を定義する式との関係を設定することもできます。 次の例には、列見出しが表示されて`FirstColumnHeading`と`SecondColumnHeading`です。 文字列`xyz`に表示される、`FirstColumnHeading`すべての行の列見出し。 次に、各製品 ID が、`Product`で一覧されているテーブル、`SecondColumnHeading`列見出し。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstColumnHeading = 'xyz',  
       SecondColumnHeading = ProductID  
FROM Production.Product;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
