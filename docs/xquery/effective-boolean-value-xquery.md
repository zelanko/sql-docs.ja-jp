---
title: 有効なブール値 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- effective Boolean value [XQuery]
- Boolean values
- XQuery, effective Boolean values
- EBV
ms.assetid: 506682b1-b6c9-45e2-aa54-7abd5844c3f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 4eb94e51896e08f60389edde0c2a6cd0461e8538
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67929958"
---
# <a name="effective-boolean-value-xquery"></a>有効なブール値 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  有効なブール値は次のとおりです。  
  
-   オペランドが空のシーケンスまたはブール値の false の場合は false。  
  
-   それ以外の場合、値は true になります。  
  
 有効なブール値は、単一のブール値、ノードシーケンス、または空のシーケンスを返す式で計算できます。 ブール値は、次の種類の式が処理されるときに暗黙的に計算されることに注意してください。  
  
-   論理式  
  
-   [Not 関数](../xquery/functions-on-boolean-values-not-function.md)  
  
-   FLWOR 式の WHERE 句  
  
-   [条件式](../xquery/conditional-expressions-xquery.md)  
  
-   [QuantifiedeExpressions](../xquery/quantified-expressions-xquery.md)  
  
 次に、有効なブール値の例を示します。 **If**式が処理されると、条件の有効なブール値が決定されます。 は`/a[1]`空のシーケンスを返すので、有効なブール値は false です。 結果は、1つのテキストノード (false) を含む XML として返されます。  
  
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
  
 型指定された**xml**列または変数に対してクエリを実行する場合は、ブール型のノードを持つことができます。 この場合の**データ ()** は、ブール値を返します。 クエリ式がブール値 true を返す場合、次の例で示すように、有効なブール値は true になります。 この例では、次のことも示しています。  
  
-   XML スキーマコレクションが作成されます。 コレクション内\<の要素 b> はブール型です。  
  
-   型指定された**xml**変数が作成され、クエリが作成されます。  
  
-   式`data(/b[1])`はブール型の true 値を返します。 したがって、この場合の有効なブール値は true です。  
  
-   式`data(/b[2])`は、ブール値の false 値を返します。 したがって、この場合の有効なブール値は false になります。  
  
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
 [FLWOR ステートメントとイテレーション &#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md)  
  
  
