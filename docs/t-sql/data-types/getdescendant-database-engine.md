---
title: "GetDescendant (データベース エンジン) |Microsoft ドキュメント"
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
- GetDescendant_TSQL
- GetDescendant
dev_langs:
- TSQL
helpviewer_keywords:
- GetDescendant [Database Engine]
ms.assetid: f5f39596-033e-4243-acbc-caa188b45b03
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ced4a5518ce7d58785a1d2954c4f131b66a5ddb0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="getdescendant-database-engine"></a>GetDescendant (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

parent の子ノードを返します。
  
## <a name="syntax"></a>構文  
  
```sql
-- Transact-SQL syntax  
parent.GetDescendant ( child1 , child2 )   
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetDescendant ( SqlHierarchyId child1 , SqlHierarchyId child2 )   
```  
  
## <a name="arguments"></a>引数  
*child1*  
NULL または**hierarchyid**の現在のノードの子です。
  
*child2*  
NULL または**hierarchyid**の現在のノードの子です。
  
## <a name="return-types"></a>戻り値の型  
**SQL Server の戻り値の型: hierarchyid**
  
**CLR の戻り値の型: SqlHierarchyId**
  
## <a name="remarks"></a>解説  
parent の子孫である 1 つの子ノードを返します。
-   parent が NULL の場合、NULL を返します。  
-   parent が NULL でなく、child1 と child2 の両方が NULL の場合、parent の子を返します。  
-   parent と child1 が NULL でなく、child2 が NULL の場合、child1 より大きい parent の子を返します。  
-   parent と child2 が NULL でなく、child1 が NULL の場合、child2 より小さい parent の子を返します。  
-   parent、child1、child2 が NULL でない場合、child1 より大きく child2 より小さい parent の子を返します。  
-   child1 が NULL でなく parent の子でない場合、例外が発生します。  
-   child2 が NULL でなく parent の子でない場合、例外が発生します。  
-   child1 >= child2 の場合は、例外が発生します。  
  
GetDescendant は決定的です。 したがって、GetDescendant が呼び出された場合、同じ入力で、同じ出力常に生成されます。 ただし、生成される子の実際の ID は、例 C に示すように、他のノードとの関係によって異なります。
  
## <a name="examples"></a>使用例  
  
### <a name="a-inserting-a-row-as-the-least-descendant-node"></a>A. 最も小さい子孫ノードとして行を挿入  
ノード `/3/1/` の既存の従業員の部下として新しい従業員が採用されました。 として新しい行のノードを指定する引数を指定せず、GetDescendant メソッドを使用して、新しい行を挿入する次のコード実行`/3/1/1/`:
  
```sql
DECLARE @Manager hierarchyid;   
SET @Manager = CAST('/3/1/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(NULL, NULL),  
'adventure-works\FirstNewEmployee', 'Application Intern', '3/11/07') ;  
```  
  
### <a name="b-inserting-a-row-as-a-greater-descendant-node"></a>B. 大きい子孫ノードとして行を挿入  
別の新しい従業員を雇用すると、レポートを A. の実行例と同じ上司ことを指定する、child 1 引数を使用して、GetDescendant メソッドを使用して、新しい行を挿入する次のコードを新しい行のノードがノードに続く例 A、になる`/3/1/2/`:
  
```sql
DECLARE @Manager hierarchyid, @Child1 hierarchyid;  
  
SET @Manager = CAST('/3/1/' AS hierarchyid);  
SET @Child1 = CAST('/3/1/1/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(@Child1, NULL),  
'adventure-works\SecondNewEmployee', 'Application Intern', '3/11/07') ;  
```  
  
### <a name="c-inserting-a-row-between-two-existing-nodes"></a>C. 既存の 2 つのノードの間に行を挿入  
3 つ目の従業員を雇用すると、例 A と同じ上司に報告します。この例より大きいノードに新しい行を挿入、 `FirstNewEmployee` 、例 A でとより小さい`SecondNewEmployee`GetDescendant メソッドを使用して、次のコード例で B. を実行します。 このコードでは、child1 引数と child2 引数の両方を使用して、新しい行のノードがノード `/3/1/1.1/` になるように指定しています。
  
```sql
DECLARE @Manager hierarchyid, @Child1 hierarchyid, @Child2 hierarchyid;  
  
SET @Manager = CAST('/3/1/' AS hierarchyid);  
SET @Child1 = CAST('/3/1/1/' AS hierarchyid);  
SET @Child2 = CAST('/3/1/2/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(@Child1, @Child2),  
'adventure-works\ThirdNewEmployee', 'Application Intern', '3/11/07') ;  
  
```  
  
例 A、B、および C を完了すると、テーブルに追加されたノード ピアになります次**hierarchyid**値。
  
`/3/1/1/`
  
`/3/1/1.1/`
  
`/3/1/2/`
  
ノード`/3/1/1.1/`ノードよりも大きい`/3/1/1/`が階層内の同じレベル。
  
### <a name="d-scalar-examples"></a>D. スカラーの例  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自由に挿入および削除のいずれかをサポートしている**hierarchyid**ノード。 GetDescendant() を使用すると、可能であれば常に任意の 2 つの間にノードを生成**hierarchyid**ノード。 次のコードを使用してサンプル ノードを生成する実行`GetDescendant`:
  
```sql
DECLARE @h hierarchyid = hierarchyid::GetRoot();  
DECLARE @c hierarchyid = @h.GetDescendant(NULL, NULL);  
SELECT @c.ToString();  
DECLARE @c2 hierarchyid = @h.GetDescendant(@c, NULL);  
SELECT @c2.ToString();  
SET @c2 = @h.GetDescendant(@c, @c2);  
SELECT @c2.ToString();  
SET @c = @h.GetDescendant(@c, @c2);  
SELECT @c.ToString();  
SET @c2 = @h.GetDescendant(@c, @c2);  
SELECT @c2.ToString();  
```  
  
### <a name="e-clr-example"></a>E. CLR の例  
次のコード スニペットの呼び出し、`GetDescendant()`メソッド。
  
```sql
SqlHierarchyId parent, child1, child2;  
parent = SqlHierarchyId.GetRoot();  
child1 = parent.GetDescendant(SqlHierarchyId.Null, SqlHierarchyId.Null);  
child2 = parent.GetDescendant(child1, SqlHierarchyId.Null);  
Console.Write(parent.GetDescendant(child1, child2).ToString());  
```  
  
## <a name="see-also"></a>参照
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[階層データ (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

