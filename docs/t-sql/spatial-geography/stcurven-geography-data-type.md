---
title: "STCurveN (geography データ型) |Microsoft ドキュメント"
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
- STCurveN
- STCurveN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveN method (geography)
ms.assetid: 99ef7100-2c4b-4f07-8d66-b343da94b023
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d33b8e6752ac8aca3bc6846a4558af4830373081
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stcurven-geography-data-type"></a>STCurveN (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定された曲線を返して、 **geography**インスタンス化されている、 **LineString**、 **CircularString**、または**CompoundCurve**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STCurveN( n )  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 **Int** 1 ~ 内の曲線の数の式、 **geography**インスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="exceptions"></a>例外  
 場合 1 < n、 **ArgumentOutOfRangeException**がスローされます。  
  
## <a name="remarks"></a>解説  
 **NULL**ときに返される次の条件が発生します。  
  
-   **Geography**インスタンスは、宣言しますが、インスタンス化されていません  
  
-   **Geography**インスタンスが空  
  
-   n が内の曲線の数を超えています、 **geography**インスタンス (を参照してください[STNumCurves (& a) #40; geography データ型 &#41;](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)  
  
-   ディメンション、 **geography**インスタンスが等しくない (を参照してください[STDimension &#40; geography データ型 &#41;](../../t-sql/spatial-geography/stdimension-geography-data-type.md)  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-stcurven-on-a-circularstring"></a>A. CircularString に対して STCurveN() を使用する  
 次の例では、2 番目の曲線を返して、 **CircularString**インスタンス。  
  
```
 DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 この例では、以下が返されます。  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve"></a>B. CompoundCurve に対して STCurveN() を使用する  
 次の例では、2 番目の曲線を返して、 **CompoundCurve**インスタンス。  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 この例では、以下が返されます。  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-containing-three-circularstrings"></a>C. 3 つの CircularStrings を含む CompoundCurve に対して STCurveN() を使用する  
 次の例では、 **CompoundCurve**を組み合わせた 3 つの異なるインスタンス**CircularString**インスタンスを同じ曲線シーケンスは、前の例として。  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE (CIRCULARSTRING (-122.358 47.653, -122.348 47.649, -122.348 47.658), CIRCULARSTRING(-122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 この例では、以下が返されます。  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
 `STCurveN()`使用する Well-Known Text (WKT) 形式に関係なく同じ結果を返します。  
  
### <a name="d-testing-for-validity-before-calling-stcurve"></a>D. STCurve() を呼び出す前に有効性をテストする  
 次の例は、ことを確認する方法を示しています。  *n*  STCurveN() メソッドを呼び出す前に有効では。  
  
```
 DECLARE @g geography;  
 DECLARE @n int;  
 SET @n = 2;  
 SET @g = geography::Parse('LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
  ```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

