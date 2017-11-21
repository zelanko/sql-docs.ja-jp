---
title: "Parse (データベース エンジン) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Parse
- Parse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Parse [Database Engine]
ms.assetid: b37e28b6-6e2e-470a-945b-ce5252da743a
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 027940c7575f3c7901cd8668879064ff375d9986
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="parse-database-engine"></a>Parse (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

正規文字列形式に変換する**hierarchyid**を**hierarchyid**値。 解析は、文字列型を変換するとき暗黙的に呼び出されます。 **hierarchyid**に発生します。 逆の役割を果たします[ToString](../../t-sql/data-types/tostring-database-engine.md)です。 Parse() は、静的メソッドです。
  
## <a name="syntax"></a>構文  
  
```sql
-- Transact-SQL syntax  
hierarchyid::Parse ( input )  
-- This is functionally equivalent to the following syntax   
-- which implicitly calls Parse():  
CAST ( input AS hierarchyid )  
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId Parse ( SqlString input )   
```  
  
## <a name="arguments"></a>引数  
*入力*  
[!INCLUDE[tsql](../../includes/tsql-md.md)] : 変換対象となる文字データ型の値。
  
CLR : 評価される String 値。
  
## <a name="return-types"></a>戻り値の型  
**SQL Server の戻り値の型: hierarchyid**
  
**CLR の戻り値の型: SqlHierarchyId**
  
## <a name="remarks"></a>解説  
解析の有効な文字列表記ではない値を受信した場合、 **hierarchyid**例外が発生します。 たとえば場合、 **char**データ型には、末尾のスペースが含まれている、例外が発生します。
  
## <a name="examples"></a>使用例  
  
### <a name="a-converting-transact-sql-values-without-a-table"></a>A. テーブルを使用しない Transact-SQL 値の変換  
次のコード例では`ToString`に変換する、 **hierarchyid**値を文字列と`Parse`文字列値を変換する、 **hierarchyid**です。
  
```sql
DECLARE @StringValue AS nvarchar(4000), @hierarchyidValue AS hierarchyid  
SET @StringValue = '/1/1/3/'  
SET @hierarchyidValue = 0x5ADE  
  
SELECT hierarchyid::Parse(@StringValue) AS hierarchyidRepresentation,  
@hierarchyidValue.ToString() AS StringRepresentation ;
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
hierarchyidRepresentation    StringRepresentation
-------------------------    -----------------------
0x5ADE                       /1/1/3/
```
  
### <a name="b-clr-example"></a>B. CLR の例  
次のコード スニペットは、Parse() メソッドを呼び出します。
  
```sql
string input = “/1/2/”;  
SqlHierarchyId.Parse(input);  
```  
  
## <a name="see-also"></a>参照
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[階層データ (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

