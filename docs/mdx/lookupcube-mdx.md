---
title: LookupCube (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ec18b600c369de872df5f6eadf06ef6c30c88efa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68098511"
---
# <a name="lookupcube-mdx"></a>LookupCube (MDX)


  同じデータベース内で別に指定されたキューブに対して評価される多次元式 (MDX) 式の値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric expression syntax  
LookupCube(Cube_Name, Numeric_Expression )  
  
String expression syntax  
LookupCube(Cube_Name, String_Expression )  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブの名前を指定する有効な文字列式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *String_Expression*  
 有効な文字列式です。通常は、文字列を返すセル座標の有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、 **lookupcube**関数は、指定されたキューブ内の指定された数値式を評価し、結果の数値を返します。  
  
 文字列式が指定されている場合、 **lookupcube**関数は、指定されたキューブ内の指定された文字列式を評価し、結果として得られる文字列値を返します。  
  
 **Lookupcube**関数は、 **lookupcube**関数を含む MDX クエリが実行されているソースキューブと同じデータベース内のキューブに対して機能します。  
  
> [!IMPORTANT]  
>  現在のクエリのコンテキストはクエリ対象のキューブに引き継がれないため、数値式または文字列式には、必要な現在のメンバーを指定する必要があります。  
  
 **Lookupcube**関数を使用した計算では、パフォーマンスが低下する可能性があります。 この関数を使用する代わりに、必要なすべてのデータが1つのキューブに存在するように、ソリューションを再設計することを検討してください。  
  
## <a name="examples"></a>例  
 次のクエリでは、LookupCube の使用方法を示しています。  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
