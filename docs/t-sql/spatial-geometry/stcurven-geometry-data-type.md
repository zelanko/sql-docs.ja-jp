---
title: "STCurveN (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveN method (geometry)
ms.assetid: 64adf1a1-3a41-41fb-b7d1-44390c3e4ea9
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd5b459bfa271d98844d30455e4e1a9e03d0e2cd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stcurven-geometry-data-type"></a>STCurveN (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

指定された曲線を返して、 **geometry**インスタンス化されている、 **LineString**、 **CircularString**、 **CompoundCurve**、または**MultiLineString**です。
  
## <a name="syntax"></a>構文  
  
```  
  
.STCurveN ( curve_index )  
```  
  
## <a name="arguments"></a>引数  
 *curve_index*  
 **Int** 1 ~ 内の曲線の数の式、 **geometry**インスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="exceptions"></a>例外  
 場合*curve_index* < 1、`ArgumentOutOfRangeException`がスローされます。  
  
## <a name="remarks"></a>解説  
 **NULL**ときに返される次のいずれかが発生します。  
  
-   **geometry**インスタンスが宣言されているが、インスタンス化されていません  
  
-   **geometry**インスタンスが空  
  
-   *curve_index*内の曲線の数を超えています、 **geometry**インスタンス  
  
-   **geometry**インスタンスが、**ポイント**、 **MultiPoint**、**多角形**、 **CurvePolygon**、または**MultiPolygon**  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-stcurven-on-a-circularstring-instance"></a>A. CircularString インスタンスに対して STCurveN() を使用する  
 次の例では、2 番目の曲線を返して、`CircularString`インスタンス。  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 このトピックの前の例では、次の値が返されます。  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve-instance-with-one-circularstring-instance"></a>B. 1 つの CircularString インスタンスを持つ CompoundCurve インスタンスに対して STCurveN() を使用する  
 次の例では、2 番目の曲線を返して、`CompoundCurve`インスタンス。  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 このトピックの前の例では、次の値が返されます。  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-instance-with-three-circularstring-instances"></a>C. 3 つの CircularString インスタンスを持つ CompoundCurve インスタンスに対して STCurveN() を使用する  
 次の例では、3 つの異なる `CompoundCurve` インスタンスを前の例と同じ曲線シーケンスに結合した `CircularString` インスタンスを使用します。  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE (CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246), CIRCULARSTRING(3 6.3246, 0 7, -3 6.3246), CIRCULARSTRING(-3 6.3246, -1 2.1082, 0 0))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 このトピックの前の例では、次の値が返されます。  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
 前の 3 つの例の結果が同じであることに注意してください。 同じ曲線シーケンスの入力にどの WKT (Well-known Text) 形式を使用しても、`STCurveN()` インスタンスを使用する場合、`CompoundCurve` によって返される結果は同じです。  
  
### <a name="d-validating-the-parameter-before-calling-stcurven"></a>D. STCurveN() を呼び出す前に、パラメーターを検証する  
 次の例は、確認する方法を示しています。`@n`を呼び出す前に有効では、`STCurveN()`メソッド。  
  
```
 DECLARE @g geometry;  
 DECLARE @n int;  
 SET @n = 3;  
 SET @g = geometry::Parse('CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
 ```  
  
## <a name="see-also"></a>参照  
 [STNumCurves &#40;geometry データ型"&"#41;](../../t-sql/spatial-geometry/stnumcurves-geometry-data-type.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


