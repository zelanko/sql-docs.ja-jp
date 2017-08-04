---
title: "LookupCube (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LOOKUPCUBE
dev_langs:
- kbMDX
helpviewer_keywords:
- LookupCube function
ms.assetid: 243fa101-328a-4016-86e0-d8b5977e15a9
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 41aed2def9e470d39f006b314f51dbb61bf63b47
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="lookupcube-mdx"></a>LookupCube (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 キューブ名を指定する有効な文字列式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *String_Expression*  
 有効な文字列式です。通常は、文字列を返すセル座標の有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、 **LookupCube**関数は、指定されたキューブ内の指定された数値式を評価し、結果として得られる数値を返します。  
  
 文字列式が指定されている場合、 **LookupCube**関数は、指定されたキューブ内の指定した文字列式を評価し、結果の文字列値を返します。  
  
 **LookupCube**を MDX クエリを実行するソース キューブが含まれているため、同じデータベース内のキューブ関数の動作、 **LookupCube**関数が実行されています。  
  
> [!IMPORTANT]  
>  現在のクエリのコンテキストはクエリ対象とするキューブに引き継がれないため、数値式または文字列式には必要な現在のメンバーを指定する必要があります。  
  
 使用するどの計算、 **LookupCube**関数は、パフォーマンスが低下する可能性があります。 この関数を使用する代わりに、必要なすべてのデータが 1 つのキューブに存在するようにソリューションを再設計することを検討してください。  
  
## <a name="examples"></a>使用例  
 次のクエリでは、LookupCube の使用方法を示しています。  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

