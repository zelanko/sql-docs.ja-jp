---
title: "もし。。。ELSE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/11/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IF_TSQL
- IF
dev_langs: TSQL
helpviewer_keywords:
- IF...ELSE keyword
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 676c881f-dee1-417a-bc51-55da62398e81
caps.latest.revision: "49"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 34a14f617d5eed0b56d6ffb44134f03efa96d2c2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="ifelse-transact-sql"></a>IF...ELSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  実行を条件を設定、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 [!INCLUDE[tsql](../../includes/tsql-md.md)] IF キーワードおよびその条件に続くステートメントが実行されるは、条件が満たされる場合。 ブール式が TRUE を返します。 オプションの ELSE キーワードは、IF 条件が満たされない (ブール式から FALSE が返される) 場合に実行される別の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
IF Boolean_expression   
     { sql_statement | statement_block }   
[ ELSE   
     { sql_statement | statement_block } ]   
```  
  
## <a name="arguments"></a>引数  
 *Boolean_expression*  
 TRUE または FALSE を返す式です。 ブール式が SELECT ステートメントを含む場合は、SELECT ステートメントをかっこで囲む必要があります。  
  
 { *sql_statement*| *statement_block* }  
 いずれかである[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはステートメントがステートメント ブロックを使用して定義されているグループ化します。 ステートメント ブロックがない限り、使用する場合、または条件が 1 つだけのパフォーマンスに影響する他[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
 ステートメント ブロックを定義するには、流れ制御キーワードの BEGIN と END を使用してください。  
  
## <a name="remarks"></a>解説  
 IF...ELSE 構造は、バッチ、ストアド プロシージャ、およびアドホック クエリ内で使うことができます。 この構造がストアド プロシージャで使用される場合、あるパラメーターの存在を調べるためによく使用されます。  
  
 IF テストは、他の IF の後、または ELSE の後で入れ子にすることができます。 入れ子のレベルの制限は、使用可能なメモリによって異なります。  
  
## <a name="example"></a>例  
  
```  
IF DATENAME(weekday, GETDATE()) IN (N'Saturday', N'Sunday')
       SELECT 'Weekend';
ELSE 
       SELECT 'Weekday';
```  
  
 例については、次を参照してください[ELSE &#40; IF しています。ELSE &#41;&#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/else-if-else-transact-sql.md)。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例で`IF…ELSE`内の項目の重み付けに基づいて、ユーザーを表示する 2 つの応答の決定、`DimProduct`テーブル。  
  
```  
-- Uses AdventureWorksDW  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct 
                  WHERE ProductKey = @productKey)   
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is too heavy to ship and is only available for pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
ELSE  
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is available for shipping or pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN...END &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [END &#40;です。作業を開始してください.終了&#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/end-begin-end-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [中に &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/while-transact-sql.md)   
 [場合 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/case-transact-sql.md)   
 [フロー制御言語 &#40;です。TRANSACT-SQL と &#41;です。](~/t-sql/language-elements/control-of-flow.md) [ELSE &#40; IF しています.ELSE &#41;&#40;です。TRANSACT-SQL と &#41; です。](../../t-sql/language-elements/else-if-else-transact-sql.md) 
  
  



