---
title: "GetAncestor (データベース エンジン) |Microsoft ドキュメント"
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
- GetAncestor_TSQL
- GetAncestor
dev_langs:
- TSQL
helpviewer_keywords:
- GetAncestor [Database Engine]
ms.assetid: b96a986f-d5e4-4034-8013-de7974594ee9
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b7649b3290175787b293ea1b720bb299ead89971
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="getancestor-database-engine"></a>GetAncestor (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **hierarchyid**を表す、  *n*番目の先祖*この*です。
  
## <a name="syntax"></a>構文  
  
```sql
-- Transact-SQL syntax  
child.GetAncestor ( n )   
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetAncestor ( int n )  
```  
  
## <a name="arguments"></a>引数  
*n*  
**Int**階層で上へ移動するレベル数を表すです。
  
## <a name="return-types"></a>戻り値の型
**SQL Server の戻り値の型: hierarchyid**
  
**CLR の戻り値の型: SqlHierarchyId**
  
## <a name="remarks"></a>解説  
出力の各ノードにとって、現在のノードが指定したレベルの先祖であるかどうかをテストするときに使用します。
  
大きい数値[GetLevel()](../../t-sql/data-types/getlevel-database-engine.md)が渡されると、NULL が返されます。
  
負の数が渡されると、例外が発生します。
  
## <a name="examples"></a>使用例  
  
### <a name="a-finding-the-child-nodes-of-a-parent"></a>A. 親の子ノードを検索する  
`GetAncestor(1)`持つ従業員を返します`david0`としてその直接の先祖 (親)。 次の例で`GetAncestor(1)`です。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(1) = @CurrentEmployee ;  
```  
  
### <a name="b-returning-the-grandchildren-of-a-parent"></a>B. 親の孫を返す  
`GetAncestor(2)`2 つのレベルがダウンして、現在のノードから、階層内にある従業員を返します。 これは現在のノードの孫にあたります。 次の例で`GetAncestor(2)`です。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\ken0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(2) = @CurrentEmployee ;  
```  
  
### <a name="c-returning-the-current-row"></a>C. 現在の行を返す  
使用して、現在のノードを返す`GetAncestor(0)`、次のコードを実行します。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(0) = @CurrentEmployee ;  
```  
  
### <a name="d-returning-a-hierarchy-level-if-a-table-is-not-present"></a>D. テーブルが存在しない場合に階層レベルを返す  
`GetAncestor` は、テーブルが存在しない場合でも、階層内の選択したレベルを返します。 たとえば、次のコードは、現在の従業員を指定しを返します、`hierarchyid`なしテーブルへの参照を現在の従業員の先祖のです。
  
```sql
DECLARE @CurrentEmployee hierarchyid ;  
DECLARE @TargetEmployee hierarchyid ;  
SELECT @CurrentEmployee = '/2/3/1.2/5/3/' ;  
SELECT @TargetEmployee = @CurrentEmployee.GetAncestor(2) ;  
SELECT @TargetEmployee.ToString(), @TargetEmployee ;  
```  
  
### <a name="e-calling-a-common-language-runtime-method"></a>E. 共通言語ランタイム メソッドを呼び出す  
次のコード スニペットの呼び出し、`GetAncestor()`メソッドです。
  
```sql
this.GetAncestor(1)  
```  
  
## <a name="see-also"></a>参照
[IsDescendantOf (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/isdescendantof-database-engine.md)  
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[階層データ (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

