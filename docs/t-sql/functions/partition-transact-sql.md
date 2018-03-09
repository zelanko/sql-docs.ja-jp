---
title: "$PARTITION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- $partition_TSQL
- $partition
dev_langs:
- TSQL
helpviewer_keywords:
- $PARTITION function
- partitions [SQL Server], numbers
ms.assetid: abc865d0-57a8-49da-8821-29457c808d2a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7fb60ef43ba359bef366a113704a784ce0f73902
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="partition-transact-sql"></a>$PARTITION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の、指定したパーティション関数に対して、パーティション分割列の値のセットがマップされるパーティション番号を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
[ database_name. ] $PARTITION.partition_function_name(expression)  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 パーティション関数を含むデータベースの名前を指定します。  
  
 *partition_function_name*  
 パーティション分割列の値のセットが適用される、既存のパーティション関数の名前を指定します。  
  
 *式 (expression)*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)のデータ型の一致か、対応するパーティション分割列のデータ型に暗黙的に変換できる必要があります。 *式*に現在参加しているパーティション分割列の名前を指定できますも*partition_function_name*です。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 $PARTITION 返します、 **int** 1 ~ パーティション関数のパーティションの数の値。  
  
 $PARTITION では、指定したパーティション関数を使用するパーティション テーブルやパーティション インデックスに値が存在しているかどうかに関係なく、有効な値に対してパーティション番号が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-getting-the-partition-number-for-a-set-of-partitioning-column-values"></a>A. パーティション分割列の値のセットに対してパーティション番号を取得する  
 次の例では、テーブルまたはインデックスを 4 つのパーティションに分割するパーティション関数 `RangePF1` を作成します。 $PARTITION がであると判断する値`10`のパーティション分割列を表す`RangePF1`テーブルのパーティション 1 に配置するとします。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE PARTITION FUNCTION RangePF1 ( int )  
AS RANGE FOR VALUES (10, 100, 1000) ;  
GO  
SELECT $PARTITION.RangePF1 (10) ;  
GO  
```  
  
### <a name="b-getting-the-number-of-rows-in-each-nonempty-partition-of-a-partitioned-table-or-index"></a>B. パーティション テーブルまたはパーティション インデックスについて、空でない各パーティション内の行数を取得する  
 次の例は、各テーブルのパーティションで行の数を返します`TransactionHistory`データが含まれます。 `TransactionHistory`テーブルがパーティション関数を使用して`TransactionRangePF1`にパーティション分割されて、`TransactionDate`列です。  
  
 この例を実行する、に対して PartitionAW.sql スクリプトを実行する必要があります最初、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]サンプル データベース。 詳細については、次を参照してください。 [PartitioningScript](http://go.microsoft.com/fwlink/?LinkId=201015)です。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT $PARTITION.TransactionRangePF1(TransactionDate) AS Partition,   
COUNT(*) AS [COUNT] FROM Production.TransactionHistory   
GROUP BY $PARTITION.TransactionRangePF1(TransactionDate)  
ORDER BY Partition ;  
GO  
```  
  
### <a name="c-returning-all-rows-from-one-partition-of-a-partitioned-table-or-index"></a>C. パーティション テーブルまたはパーティション インデックスの 1 つのパーティションからすべての行を返す  
 次の例では、テーブル `5` のパーティション `TransactionHistory` 内にあるすべての行を返します。  
  
> [!NOTE]  
>  この例を実行する、に対して PartitionAW.sql スクリプトを実行する必要があります最初、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]サンプル データベース。 詳細については、次を参照してください。 [PartitioningScript](http://go.microsoft.com/fwlink/?LinkId=201015)です。  
  
```  
SELECT * FROM Production.TransactionHistory  
WHERE $PARTITION.TransactionRangePF1(TransactionDate) = 5 ;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)  
  
  
