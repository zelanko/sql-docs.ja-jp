---
title: "STRelate (geometry データ型) | Microsoft Docs"
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
- STRelate (geometry Data Type)
- STRelate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRelate (geometry Data Type)
ms.assetid: 9dcb5f58-35ab-4bb3-86ee-2d29eefba6d3
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: beb2ce0ebcba2c290dbb56d6df62a820734871cd
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="strelate-geometry-data-type"></a>STRelate (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  任意の **geometry** インスタンスと別の **geometry** インスタンスとの間になんらかの関係がある場合は 1 を返します。ここでの関係は、Dimensionally Extended 9 Intersection Model (DE-9IM) パターンのマトリックス値で定義されます。関係がない場合は 0 を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STRelate ( other_geometry, intersection_pattern_matrix )  
```  
  
## <a name="arguments"></a>引数  
 *other_geometry*  
 `STRelate()` を呼び出したインスタンスと比較される、別の **geometry** インスタンスです。  
  
 *intersection_pattern_matrix*  
 **nchar(9)** 型の文字列です。2 つの **geometry** インスタンスの間にある、DE-9IM パターンのマトリックス デバイスで受け付けることができる値にエンコードされます。  
  
## <a name="remarks"></a>Remarks  
 **geometry** インスタンスの SRID (spatial reference ID) が一致しない場合、このメソッドは常に null を返します。 このメソッドは、マトリックスが整形式でない場合に、**ArgumentException** をスローします。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **bit**  
  
 CLR 戻り値の型: **SqlBoolean**  
  
## <a name="examples"></a>使用例  
 `STRelate()` を使用して、空間的に連結されていない 2 つの **geometry** インスタンスが明示的に DE-9IM パターンを使用しているかどうかをテストする例を次に示します。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(5 5)', 0);  
SELECT @g.STRelate(@h, 'FF*FF****');  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
