---
title: "STSymDifference (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
f1_keywords:
- STSymDifference_TSQL
- STSymDifference (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STSymDifference (geometry Data Type)
ms.assetid: 1d4cf35a-ca89-4aa4-ae30-e61a0ff18b53
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3bedfb8a5cc4eb2ca0963bbfe2454a3ed1508c0
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stsymdifference-geometry-data-type"></a>STSymDifference (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  いずれかであるすべてのポイントを表すオブジェクトを返します**geometry**インスタンスと別**geometry**インスタンスが両方のインスタンスに存在する地点されません。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STSymDifference ( other_geometry )  
```  
  
## <a name="arguments"></a>引数  
 *other_geometry*  
 もう 1 つ**geometry**インスタンスをインスタンス`STSymDistance()`が呼び出されています。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 このメソッドは、場合常に null を返しますの spatial reference Id (Srid)、 **geometry**インスタンスが一致しません。 結果に円弧が含まれるのは、入力インスタンスに円弧が含まれる場合のみです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-computing-the-symmetric-difference-of-two-polygon-instances"></a>A. 2 つの Polygon インスタンスの対称差を計算する  
 次の例で`STSymDifference()`2 つの対称差を計算する`Polygon`インスタンス。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STSymDifference(@h).ToString();  
```  
  
### <a name="b-computing-the-symmetric-difference-between-a-curvepolygon-and-a-polygon-instance"></a>B. CurvePolygon インスタンスと Polygon インスタンスの対称差を計算する  
 次の例は、`GeometryCollection` と `CurvePolygon` の間の対称差を表す `Polygon` を返します。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 SELECT @h.STSymDifference(@g).ToString();
 ```  
  
## <a name="c-using-stsymdifference-on-curvepolygon-instance-with-an-inscribed-polygon-instance"></a>C. Polygon インスタンスが内接する CurvePolygon インスタンスで STSymDifference() を使用する  
 次の例を返します、 `CurvePolygon` 、内部使用インスタンス`Polygon`を比較する 2 つのインスタンス間の対称差を表すリングします。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 2 -1, 2 1, 1 1, 1 -1))';  
 SELECT @h.STSymDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
