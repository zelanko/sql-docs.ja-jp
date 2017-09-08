---
title: "ShortestLineTo (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ShortestLineTo_TSQL
- ShortestLineTo
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geography)
ms.assetid: 9d7c9885-5d1b-49ae-af31-5ef9fb8acaba
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: acb6d16fbf1413a81a05582bc203a7e768b70c75
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="shortestlineto-geography-data-type"></a>ShortestLineTo (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  返します、 **LineString**を 2 つの間の最短距離を表す 2 つの点を持つインスタンス**geography**インスタンス。 長さ、 **LineString**返されるインスタンスは、2 つの間の距離**geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.ShortestLineTo ( geography_other )  
```  
  
## <a name="arguments"></a>引数  
 *geography_other*  
 2 番目の指定**geography**インスタンスが、呼び出し元**geography**インスタンスが最短距離を調べるましょう。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 このメソッドを返します、 **LineString**インスタンス、2 つの交差しないの境界上にあるエンドポイントを持つ**geography**比較対象となるインスタンスです。 長さ、 **LineString**返されたが、2 つの間で短距離**geography**インスタンス。 空**LineString**インスタンスが返される 2 つ**geography**互いに交差するインスタンス。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. 交差しないインスタンスに対して ShortestLineTo() を呼び出す  
 この例は、間の最短距離を検索、`CircularString`インスタンスおよび`LineString`インスタンスを返す、 `LineString` 2 つの点を結ぶインスタンス。  
  
 `DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';`  
  
 `DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)';`  
  
 `SELECT @g1.ShortestLineTo(@g2).ToString();`  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. 交差するインスタンスに対して ShortestLineTo() を呼び出す  
 次の例では、`LineString` インスタンスが `LineString` インスタンスと交差しているため、空の `CircularString` インスタンスが返されます。  
  
 `DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';`  
  
 `DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.348 47.649, -122.681 47.655)';`  
  
 `SELECT @g1.ShortestLineTo(@g2).ToString();`  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
