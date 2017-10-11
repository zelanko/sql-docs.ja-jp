---
title: "CollectionAggregate (geometry データ型) |Microsoft ドキュメント"
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
- CollectionAggregate method (geometry)
ms.assetid: b7c85d59-c841-4b7f-9d46-8b4b7f2a3afe
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2acf5b0fe7f3b6833f56f5264844e4dc9870155f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="collectionaggregate-geometry-data-type"></a>CollectionAggregate (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

作成、 **GeometryCollection**インスタンスのセットから**geometry**型です。
  
## <a name="syntax"></a>構文  
  
```  
  
CollectionAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>引数  
 *geometry_operand*  
 **Geometry**型のテーブル列のセットを表す**geometry**に記述するオブジェクト、 **GeometryCollection**インスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
## <a name="exceptions"></a>例外  
 入力値が無効である場合は、`FormatException` をスローします。 参照してください[STIsValid (& a) #40; geometry データ型 &#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
## <a name="remarks"></a>解説  
 メソッドを返します。 **null**入力が空または入力がの Srid が異なる場合。 参照してください[空間参照識別子 & #40 です。Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 メソッドは無視**null**入力します。  
  
> [!NOTE]  
>  メソッドを返します。 **null**入力されたすべての値が場合**null**です。  
  
## <a name="examples"></a>使用例  
 次の例は、`GeometryCollection` と `CurvePolygon` が含まれる `Polygon` インスタンスを返します。  
  
 ```
 -- Setup table variable for CollectionAggregate example  
 DECLARE @Geom TABLE  
 (  
 shape geometry,  
 shapeType nvarchar(50)  
 )  
 INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'),  
 ('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle');  
 -- Perform CollectionAggregate on @Geom.shape column  
 SELECT geometry::CollectionAggregate(shape).ToString()  
 FROM @Geom;
 ```  
  
## <a name="see-also"></a>参照  
 [拡張された静的なジオメトリ メソッド](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


