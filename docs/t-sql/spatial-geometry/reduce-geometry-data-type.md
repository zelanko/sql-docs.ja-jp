---
title: "(Geometry データ型) を削減 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs:
- TSQL
helpviewer_keywords:
- Reduce method
ms.assetid: 132184bf-c4d2-4a27-900d-8373445dce2a
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6e74a2a16806741dda7171ec0327b709fb697cb9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="reduce-geometry-data-type"></a>Reduce (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

近似を返します、指定された**geometry**インスタンスは指定された許容範囲を持つインスタンスに対して Douglas-peucker アルゴリズムの拡張機能を実行して生成します。
  
## <a name="syntax"></a>構文  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>引数  
 *許容範囲*  
 型の値は、 **float**です。 *トレランス*は、近似アルゴリズムに入力する許容範囲です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 コレクション型のこのアルゴリズムは個別に各**geometry**インスタンスに含まれています。  
  
 このアルゴリズムは変更されません**ポイント**インスタンス。  
  
 **LineString**、 **CircularString**、および**CompoundCurve**インスタンス、近似アルゴリズムは、元の始点と、インスタンスの終点が保持されますと。追加、ポイントから、元のインスタンスの地点の結果から最も離れたを超えない、指定された許容範囲です。  
  
 `Reduce()`返します、 **LineString**、 **CircularString**、または**CompoundCurve**インスタンス**CircularString**インスタンス。  `Reduce()`どちらかを返します、 **CompoundCurve**または**LineString**インスタンス**CompoundCurve**インスタンス。  
  
 **多角形**各リングにインスタンスでは、近似アルゴリズムが個別に適用されます。 メソッドが生成されます、`FormatException`場合、返された**多角形**インスタンスが無効ですたとえば、有効でない**MultiPolygon**場合インスタンスが作成`Reduce()`それぞれを簡略化に適用されます。インスタンスのリングし、結果として得られるリングが重なっています。  **CurvePolygon**インスタンス外部リングと内部リングがない、`Reduce()`を返します、 **CurvePolygon**、 **LineString**、または**ポイント**インスタンス。  場合、 **CurvePolygon**内部リングを持つ、 **CurvePolygon**または**MultiPoint**インスタンスが返されます。  
  
 円弧が検出されると、指定された許容範囲の半分以内で弦によって円弧を近似できるかどうかが近似アルゴリズムによってチェックされます。  弦がこの条件を満たす場合、円弧は計算において弦で置き換えられます。 弦がこの条件を満たしていない場合は、円弧が保持され、近似アルゴリズムが残りのセグメントに適用されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-reduce-to-simplify-a-linestring"></a>A. Reduce() を使用して LineString を簡略化する  
 次の例を作成、`LineString`使用して、インスタンス`Reduce()`のインスタンスを簡略化します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0, 2 1, 3 0, 4 1)', 0);  
SELECT @g.Reduce(.75).ToString();  
```  
  
### <a name="b-using-reduce-with-varying-tolerance-levels-on-a-circularstring"></a>B. CircularString に対し許容レベルを変えて Reduce() を使用する  
 次の例で`Reduce()`3 つの許容レベルで、 **CircularString**インスタンス。  
  
 `DECLARE @g geometry = 'CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0)';`  
  
 `SELECT @g.Reduce(5).ToString();`  
  
 `SELECT @g.Reduce(15).ToString();`  
  
 `SELECT @g.Reduce(16).ToString();`  
  
 この例の結果は、次のようになります。  
  
 `CIRCULARSTRING (0 0, 8 8, 16 0, 20 -4, 24 0)`  
  
 `COMPOUNDCURVE (CIRCULARSTRING (0 0, 8 8, 16 0), (16 0, 24 0))`  
  
 `LINESTRING (0 0, 24 0)`  
  
 返されるそれぞれのインスタンスには、終点 (0 0) と (24 0) が含まれます。  
  
### <a name="c-using-reduce-with-varying-tolerance-levels-on-a-compoundcurve"></a>C. CompoundCurve に対し許容レベルを変えて Reduce() を使用する  
 次の例で`Reduce()`2 つの許容レベルで、 **CompoundCurve**インスタンス。  
  
 `DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0),(24 0, 20 4, 16 0))';`  
  
 `SELECT @g.Reduce(15).ToString();`  
  
 `SELECT @g.Reduce(16).ToString();`  
  
 この例では、2 つ目**選択**ステートメントから返される、 **LineString**インスタンス:`LineString(0 0, 16 0)`です。  
  
### <a name="showing-an-example-where-the-original-start-and-end-points-are-lost"></a>元の始点と終点が失われる例  
 次の例では、元の始点と終点が結果のインスタンスで保持されない状況を示します。 元の始点を維持するためにこれが発生し、無効な終了点になる**LineString**インスタンス。  
  
```  
DECLARE @g geometry = 'LINESTRING(0 0, 4 0, 2 .01, 1 0)';  
DECLARE @h geometry = @g.Reduce(1);  
SELECT @g.STIsValid() AS Valid  
SELECT @g.ToString() AS Original, @h.ToString() AS Reduced;  
```  
  
## <a name="see-also"></a>参照  
 [拡張された静的なジオメトリ メソッド](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


