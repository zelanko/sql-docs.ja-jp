---
title: "有効なブール値 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- effective Boolean value [XQuery]
- Boolean values
- XQuery, effective Boolean values
- EBV
ms.assetid: 506682b1-b6c9-45e2-aa54-7abd5844c3f1
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 59a985af62266817e66667b91c4e766123f808e2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="effective-boolean-value-xquery"></a>有効なブール値 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  次に有効なブール値を示します。  
  
-   オペランドが空のシーケンスまたはブール型の false である場合、false になります。  
  
-   それ以外の場合、値は true になります。  
  
 有効なブール値は、1 つのブール値、ノード シーケンス、または空のシーケンスを返す式で計算できます。 次の型の式が処理されるとき、ブール値が暗黙的に計算されます。  
  
-   論理式  
  
-   [機能しません。](../xquery/functions-on-boolean-values-not-function.md)  
  
-   FLWOR 式の WHERE 句  
  
-   [条件式](../xquery/conditional-expressions-xquery.md)  
  
-   [QuantifiedeExpressions](../xquery/quantified-expressions-xquery.md)  
  
 次に、有効なブール値の例を示します。 ときに、**場合**式が処理されると、現在の状態の有効なブール値が決定されます。 `/a[1]` 、空のシーケンスを返す有効なブール値は false。 1 つのテキスト ノード (false) を含む XML として結果が返されます。  
  
```  
value is false  
DECLARE @x XML  
SET @x = '<b/>'  
SELECT @x.query('if (/a[1]) then "true" else "false"')  
go  
```  
  
 次の例では、式が空ではないシーケンスを返すので、有効なブール値は true になります。  
  
```  
DECLARE @x XML  
SET @x = '<a/>'  
SELECT @x.query('if (/a[1]) then "true" else "false"')  
go  
```  
  
 ときに型指定されたクエリを実行する**xml**列または変数、ブール型のノードを持つことができます。 **Data()**ここではブール値を返します。 クエリ式がブール値 true を返す場合、次の例で示すように、有効なブール値は true になります。 この例では、次のことも示しています。  
  
-   XML スキーマ コレクションが作成されます。 要素\<b > コレクションではブール型です。  
  
-   型指定された**xml**変数が作成され、クエリを実行します。  
  
-   式`data(/b[1])`ブール値 true を返します。 したがって、この場合の有効なブール値は true になります。  
  
-   式`data(/b[2])`ブール値 false を返します。 したがって、この場合の有効なブール値は false になります。  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="s" type="string"/>  
      <element name="b" type="boolean"/>  
</schema>'  
go  
DECLARE @x XML(SC)  
SET @x = '<b>true</b><b>false</b>'  
SELECT @x.query('if (data(/b[1])) then "true" else "false"')  
SELECT @x.query('if (data(/b[2])) then "true" else "false"')  
go  
```  
  
## <a name="see-also"></a>参照  
 [XQuery の基礎](../xquery/xquery-basics.md)   
 [FLWOR ステートメントおよびイテレーション &#40;です。XQuery と #41 です。](../xquery/flwor-statement-and-iteration-xquery.md)  
  
  
