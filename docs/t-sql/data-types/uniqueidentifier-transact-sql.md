---
title: "一意識別子 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/1/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- uniqueidentifier
- uniqueidentifier_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- globally unique identifiers [SQL Server]
- GUIDs [SQL Server]
ms.assetid: b026035b-f3d2-4d70-989d-3884b4ca0233
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 76f7a3c784c0d05e1a6f94da0b33207bfbb1efec
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="uniqueidentifier-transact-sql"></a>uniqueidentifier (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

16 バイトの GUID です。
  
## <a name="remarks"></a>解説  
列またはのローカル変数**uniqueidentifier**データ型は、次の方法で値に初期化することができます。
-   使用して、 [NEWID](../../t-sql/functions/newid-transact-sql.md)または[NEWSEQUENTIALID](../../t-sql/functions/newsequentialid-transact-sql.md)関数。    
-   形式で文字列定数を変換することで*xxxxxxxx*-*xxxx*-*xxxx*-*xxxx*-*して*、各*x*は 0 ~ 9 または a ~ f の 16 進数字です。 たとえば、6F9619FF-8B86-D011-B42D-00C04FC964FF は有効な**uniqueidentifier**値。  
  
比較演算子で使用できます**uniqueidentifier**値。 ただし、2 つの値のビット パターンを比較することによる順序付けは行われません。 に対して実行できる操作のみ、 **uniqueidentifier**値には比較 (=、<>、 \<、>、 \<=、> =) と NULL (IS NULL と IS NOT NULL) をチェックします。 他の算術演算子は使用できません。 すべての列制約と、IDENTITY 以外のプロパティで使用できます、 **uniqueidentifier**データ型。
  
マージ レプリケーションおよびトランザクション レプリケーションでサブスクリプションを使用して更新**uniqueidentifier**確実行がテーブルの複数のコピー間で一意に識別するために列です。
  
## <a name="converting-uniqueidentifier-data"></a>uniqueidentifier データの使用  
**Uniqueidentifier**型と見なされます、文字の種類、文字式からの変換のためであるため、文字型に変換する場合は切り捨てルールの対象です。 つまり、文字式を異なるサイズの文字型に変換する場合、値が新しいデータ型にとって長すぎるときは、切り捨てられます。 「使用例」を参照してください。
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項

これらのツールおよび機能をサポートしていない、`uniqueidentifier`データ型。
- PolyBase
- [dwloader の読み込みツール](https://msdn.microsoft.com/sql/analytics-platform-system/dwloader)Parallel Data Warehouse の

## <a name="examples"></a>使用例  
次の例では、`uniqueidentifier` 型の値を `char` 型の値に変換します。
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
次の例は、変換後のデータ型に対して値が長すぎる場合のデータの切り捨てを示します。 **Uniqueidentifier**型は 36 文字に制限されて、その長さを超える文字は切り捨てられます。
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[NEWID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/newid-transact-sql.md)  
[NEWSEQUENTIALID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/newsequentialid-transact-sql.md)    
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)
  
  
