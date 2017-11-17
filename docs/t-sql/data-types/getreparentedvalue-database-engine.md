---
title: "GetReparentedValue (データベース エンジン) |Microsoft ドキュメント"
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
- Reparent_TSQL
- Reparent
dev_langs:
- TSQL
helpviewer_keywords:
- Reparent [Database Engine]
ms.assetid: f47f8e25-08ef-498b-84f4-a317aca1f358
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57f565258c7fd95347d7d9bd36b2dd2034712efe
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="getreparentedvalue-database-engine"></a>GetReparentedValue (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

ルートからのパスは、パスのノードを返しますに*ページャー*からのパスと、その後*oldRoot*に*この*です。
  
## <a name="syntax"></a>構文  
  
```sql
-- Transact-SQL syntax  
node. GetReparentedValue ( oldRoot, newRoot )  
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetReparentedValue ( SqlHierarchyId oldRoot , SqlHierarchyId newRoot )  
```  
  
## <a name="arguments"></a>引数  
*oldRoot*  
A **hierarchyid**を変更するのには、階層のレベルを表すノードはします。
  
*してページャー*  
A **hierarchyid**入れ替えられるノードを表す、 *oldRoot*ノードを移動するために現在のノードのセクションでします。
  
## <a name="return-types"></a>戻り値の型  
**SQL Server の戻り値の型: hierarchyid**
  
**CLR の戻り値の型: SqlHierarchyId**
  
## <a name="remarks"></a>解説  
ノードを移動して、ツリーを変更するために使用する*oldRoot*に*ページャー*です。 GetReparentedValue を使用すると、ある階層のノードを階層内の新しい位置に移動できます。 **Hierarchyid**データ型を表しますが、階層構造は強制されません。 ユーザーは、hierarchyid が新しい位置に対して正しく構成されていることを確認する必要があります。 一意のインデックス、 **hierarchyid**データ型のエントリの重複を防ぐのに役立ちます。 サブツリー全体を移動の例は、次を参照してください。[階層データ & #40 です。SQL Server &#41;](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>使用例  
  
### <a name="a-comparing-two-node-locations"></a>A. 2 つのノードの位置の比較  
次の例は、ノードの現在の hierarchyid と、 表示、 **hierarchyid**ノードのなりますの子孫に移動したかどうか、  **@NewParent** ノード。 この例では、`ToString()` メソッドを使用して階層関係を表示しています。
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ;  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- who is /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- who is /2/3/  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
(@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) ).ToString() AS Proposed_OrgNode_AS_Text,  
OrgNode AS Current_OrgNode,  
@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) AS Proposed_OrgNode,  
*  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = @SubjectEmployee ;  
GO  
```  
  
### <a name="b-updating-a-node-to-a-new-location"></a>B. 新しい位置へのノードの更新  
次の例では`GetReparentedValue()`ノードを元の場所から、階層内の新しい場所に移動する UPDATE ステートメントで。
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ; -- Node /1/1/2/  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- Node /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- Node /2/3/  
  
UPDATE HumanResources.EmployeeDemo  
SET OrgNode = @SubjectEmployee. GetReparentedValue(@OldParent, @NewParent)   
WHERE OrgNode = @SubjectEmployee ;  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
*  
FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\gail0' ; -- Now node /2/3/2/  
```  
  
### <a name="c-clr-example"></a>C. CLR の例  
次のコード スニペットは、GetReparentedValue () メソッドを呼び出します。
  
```sql
this. GetReparentedValue(oldParent, newParent)  
```  
  
## <a name="see-also"></a>参照
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[階層データ (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

