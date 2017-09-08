---
title: "UnionAggregate (geometry データ型) |Microsoft ドキュメント"
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
- UnionAggregate method (geometry)
ms.assetid: dc7929cc-55ca-4a2c-a4b9-f5452f95bde8
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 65759e7e4d7701b36d79b8ce27bb5bfe176ba3e3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="unionaggregate-geometry-data-type"></a>UnionAggregate (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

geometry オブジェクトのセットに対して和集合演算を実行します。
  
## <a name="syntax"></a>構文  
  
```  
  
UnionAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>引数  
 *geometry_operand*  
 **Geometry**型のテーブル列のセットを保持する**geometry**和集合演算を実行するオブジェクト。  
  
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
 次の例は、一連の和集合を返します**geometry**テーブル変数内のオブジェクト。  
  
 `-- Setup table variable for UnionAggregate example`  
  
 `DECLARE @Geom TABLE`  
  
 `(`  
  
 `shape geometry,`  
  
 `shapeType nvarchar(50)`  
  
 `);`  
  
 `INSERT INTO @Geom(shape,shapeType)`  
  
 `VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'),`  
  
 `('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle');`  
  
 `-- Perform UnionAggregate on @Geom.shape column`  
  
 `SELECT geometry::UnionAggregate(shape).ToString()`  
  
 `FROM @Geom;`  
  
## <a name="see-also"></a>参照  
 [拡張された静的なジオメトリ メソッド](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


