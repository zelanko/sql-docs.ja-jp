---
title: "ShortestLineTo (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geometry)
ms.assetid: 39a2d0e4-4f93-4e94-a27e-6ad9537cfe74
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bc8843ceefe8819d2f314d76b019720863866ed1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="shortestlineto-geometry-data-type"></a>ShortestLineTo (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

返します、 **LineString**を 2 つの間の最短距離を表す 2 つの点を持つインスタンス**geometry**インスタンス。 長さ、 **LineString**返されるインスタンスは、2 つの間の距離**geometry**インスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.ShortestLineTo ( geometry_other )  
```  
  
## <a name="arguments"></a>引数  
 *geometry_other*  
 2 番目**geometry**インスタンスが、呼び出し元**geometry**インスタンスが最短距離を調べるましょう。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 このメソッドを返します、 **LineString**インスタンス、2 つの交差しないの境界上にあるエンドポイントを持つ**geometry**比較対象となるインスタンスです。 長さ、 **LineString**返されたが、2 つの間で短距離**geometry**インスタンス。 空**LineString**インスタンスが返される 2 つ**geometry**互いに交差するインスタンス。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. 交差しないインスタンスに対して ShortestLineTo() を呼び出す  
 この例は、間の最短距離を検索、`CircularString`インスタンスおよび`LineString`インスタンスを返す、 `LineString` 2 つの点を結ぶインスタンス。  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(-4 7, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. 交差するインスタンスに対して ShortestLineTo() を呼び出す  
 次の例では、`LineString` インスタンスが `LineString` インスタンスと交差しているため、空の `CircularString` インスタンスが返されます。  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(0 5, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
## <a name="see-also"></a>参照  
 [ShortestLineTo &#40;geography データ型"&"#41;](../../t-sql/spatial-geography/shortestlineto-geography-data-type.md)  
  
  


