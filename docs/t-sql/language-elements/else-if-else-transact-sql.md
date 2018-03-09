---
title: "(場合に. その他。その他) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ELSE
- ELSE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 6f2b4278-0dea-4603-bbd3-7cbad602a645
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: ca282df7272f2eeffe1afc50238a41f69c7b615f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="else-ifelse-transact-sql"></a>ELSE (IF...ELSE) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  実行を条件を設定、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント (*sql_statement*) 次、 *Boolean_expression*場合に実行される、 *Boolean_expression*を TRUE に評価します。 オプションの ELSE キーワードは、代替[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが実行すると実行*Boolean_expression* FALSE または NULL に評価します。  
  
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
 TRUE または FALSE を返す式です。 場合、 *Boolean_expression* SELECT ステートメントを含む SELECT ステートメントをかっこで囲む必要があります。  
  
 { *sql_statement* | *statement_block* }  
 有効な[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはステートメント ブロックで定義されているグループ化します。 ステートメント ブロック (バッチ) を定義するのには、BEGIN と END は、フロー制御言語キーワードを使用します。 すべて[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは内では、開始しています.終了ブロックする場合に、特定[!INCLUDE[tsql](../../includes/tsql-md.md)]同じバッチ (ステートメント ブロック) 内で一緒にグループ化できないステートメントもする必要があります。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-a-simple-boolean-expression"></a>A. 簡単なブール式を使用する  
 次の例が簡単なブール式 (`1=1`) が true であり、そのため、最初のステートメントを出力します。  
  
```  
IF 1 = 1 PRINT 'Boolean_expression is true.'  
ELSE PRINT 'Boolean_expression is false.' ;  
```  
  
 次の例が簡単なブール式 (`1=2`) が false の場合、そのため、2 番目のステートメントを出力します。  
  
```  
IF 1 = 2 PRINT 'Boolean_expression is true.'  
ELSE PRINT 'Boolean_expression is false.' ;  
GO  
```  
  
### <a name="b-using-a-query-as-part-of-a-boolean-expression"></a>B. クエリをブール式の一部として使用する  
 次の例では、クエリをブール式の一部として実行します。 `Product` テーブルには `WHERE` 句を満たす自転車が 10 台あるため、最初の print ステートメントが実行されます。 どのような場合に 2 番目のステートメントが実行されるかを確認するには、`> 5` を `> 15` に変更します。  
  
```  
USE AdventureWorks2012;  
GO  
IF   
(SELECT COUNT(*) FROM Production.Product WHERE Name LIKE 'Touring-3000%' ) > 5  
PRINT 'There are more than 5 Touring-3000 bicycles.'  
ELSE PRINT 'There are 5 or less Touring-3000 bicycles.' ;  
GO  
```  
  
### <a name="c-using-a-statement-block"></a>C. ステートメント ブロックを使用する  
 次の例では、クエリをブール式の一部として実行してから、ブール式の結果に基づいて若干異なるステートメント ブロックを実行します。 各ステートメント ブロックが始まる`BEGIN`で終わります`END`です。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @AvgWeight decimal(8,2), @BikeCount int  
IF   
(SELECT COUNT(*) FROM Production.Product WHERE Name LIKE 'Touring-3000%' ) > 5  
BEGIN  
   SET @BikeCount =   
        (SELECT COUNT(*)   
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%');  
   SET @AvgWeight =   
        (SELECT AVG(Weight)   
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%');  
   PRINT 'There are ' + CAST(@BikeCount AS varchar(3)) + ' Touring-3000 bikes.'  
   PRINT 'The average weight of the top 5 Touring-3000 bikes is ' + CAST(@AvgWeight AS varchar(8)) + '.';  
END  
ELSE   
BEGIN  
SET @AvgWeight =   
        (SELECT AVG(Weight)  
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%' );  
   PRINT 'Average weight of the Touring-3000 bikes is ' + CAST(@AvgWeight AS varchar(8)) + '.' ;  
END ;  
GO  
```  
  
### <a name="d-using-nested-ifelse-statements"></a>D. 入れ子になった IF...ELSE ステートメントを使用する  
 次の例では、IF のかを示します。 別の内部は、ELSE ステートメントを入れ子にすることができます。 各ステートメントをテストするには、`@Number` 変数を `5`、`50`、および `500` に設定します。  
  
```  
DECLARE @Number int;  
SET @Number = 50;  
IF @Number > 100  
   PRINT 'The number is large.';  
ELSE   
   BEGIN  
      IF @Number < 10  
      PRINT 'The number is small.';  
   ELSE  
      PRINT 'The number is medium.';  
   END ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-a-query-as-part-of-a-boolean-expression"></a>E: ブール式の一部としてクエリを使用します。  
 次の例で`IF…ELSE`内の項目の重み付けに基づいて、ユーザーを表示する 2 つの応答の決定、`DimProduct`テーブル。  
  
```  
-- Uses AdventureWorks  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct WHERE ProductKey=@productKey)   
    (SELECT @productKey, EnglishDescription, Weight, 'This product is too heavy to ship and is only available for pickup.' FROM DimProduct WHERE ProductKey=@productKey)  
ELSE  
    (SELECT @productKey, EnglishDescription, Weight, 'This product is available for shipping or pickup.' FROM DimProduct WHERE ProductKey=@productKey)  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [フロー制御言語 &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)  
  
  


