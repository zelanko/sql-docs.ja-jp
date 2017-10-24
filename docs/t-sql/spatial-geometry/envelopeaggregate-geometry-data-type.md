---
title: "EnvelopeAggregate (geometry データ型) |Microsoft ドキュメント"
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
- EnvelopeAggregate method (geometry)
ms.assetid: c4c15abe-0fe9-441d-9d42-6572e264869c
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f6bf9a42f6d41973f2abed3377c5a311271e106f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="envelopeaggregate-geometry-data-type"></a>EnvelopeAggregate (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

指定されたセットの境界ボックスを返します**geometry**オブジェクト。
  
## <a name="syntax"></a>構文  
  
```  
  
EnvelopeAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>引数  
 *geometry_operand*  
 **Geometry**型のテーブル列のセットを表す**geometry**オブジェクト。  
  
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
 次の例は、テーブル変数列のオブジェクトのセットの境界ボックスを返します。  
  
 ```
 -- Setup table variable for EnvelopeAggregate example 
DECLARE @Geom TABLE 
( 
shape geometry, 
shapeType nvarchar(50) 
) 
INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'), 
('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle'); 
-- Perform EnvelopeAggregate on @Geom.shape column 
SELECT geometry::EnvelopeAggregate(shape).ToString() 
FROM @Geom;
 ```  
  
## <a name="see-also"></a>参照  
 [拡張された静的なジオメトリ メソッド](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


