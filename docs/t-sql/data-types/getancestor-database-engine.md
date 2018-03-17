---
title: "GetAncestor (データベース エンジン) | Microsoft Docs"
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b232238dccf5c22918a8805cdc9cd876dfef5723
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="getancestor-database-engine"></a>GetAncestor (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

*this* の *n*番目の先祖を表す **hierarchyid** が返されます。
  
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
n、 **int**, を階層を上がるレベル数を表します。
  
## <a name="return-types"></a>戻り値の型
**SQL Server の戻り値の型: * *hierarchyid * ***
  
**CLR 戻り値の型:SqlHierarchyId**
  
## <a name="remarks"></a>Remarks  
出力の各ノードにとって、現在のノードが指定したレベルの先祖であるかどうかをテストするときに使用します。
  
[GetLevel()](../../t-sql/data-types/getlevel-database-engine.md) より大きい数値が渡されると、NULL が返されます。
  
負の数が渡されると、例外が発生します。
  
## <a name="examples"></a>使用例  
  
### <a name="a-finding-the-child-nodes-of-a-parent"></a>A. 親の子ノードを検索する  
`GetAncestor(1)` は、`david0` をその直接の先祖 (親) とする従業員を返します。 `GetAncestor(1)` の使用例を次に示します。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(1) = @CurrentEmployee ;  
```  
  
### <a name="b-returning-the-grandchildren-of-a-parent"></a>B. 親の孫を返す  
`GetAncestor(2)` は、階層内で現在のノードより 2 つ下のレベルにある従業員を返します。 これは現在のノードの孫にあたります。 `GetAncestor(2)` の使用例を次に示します。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\ken0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(2) = @CurrentEmployee ;  
```  
  
### <a name="c-returning-the-current-row"></a>C. 現在の行を返す  
`GetAncestor(0)` を使用して現在のノードを返すには、次のコードを実行します。
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(0) = @CurrentEmployee ;  
```  
  
### <a name="d-returning-a-hierarchy-level-if-a-table-is-not-present"></a>D. テーブルが存在しない場合に階層レベルを返す  
`GetAncestor` は、テーブルが存在しない場合でも、階層内の選択したレベルを返します。 たとえば、次のコードでは、現在の従業員を指定し、テーブルを参照せずに現在の従業員の先祖の `hierarchyid` を返します。
  
```sql
DECLARE @CurrentEmployee hierarchyid ;  
DECLARE @TargetEmployee hierarchyid ;  
SELECT @CurrentEmployee = '/2/3/1.2/5/3/' ;  
SELECT @TargetEmployee = @CurrentEmployee.GetAncestor(2) ;  
SELECT @TargetEmployee.ToString(), @TargetEmployee ;  
```  
  
### <a name="e-calling-a-common-language-runtime-method"></a>E. 共通言語ランタイム メソッドを呼び出す  
次のコード例では `GetAncestor()` メソッドを呼び出します。
  
```sql
this.GetAncestor(1)  
```  
  
## <a name="see-also"></a>参照
[IsDescendantOf &#40;データベース エンジン"&"#41 です。](../../t-sql/data-types/isdescendantof-database-engine.md)  
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[階層データ (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
