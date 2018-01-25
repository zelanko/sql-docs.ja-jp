---
title: "InstanceOf (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs: TSQL
helpviewer_keywords: InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c53e66f85d614b79e51312dc4404fd19acd69fed
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

場合にテストするメソッド、 **geometry**インスタンスが指定した型と同じです。 場合 1 を返しますの種類、 **geometry**インスタンスは、指定された型と同じまたは指定した型が、インスタンスの型の先祖である場合は、0 を返しますそれ以外の場合。
  
## <a name="syntax"></a>構文  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>引数  
 *geometry_type*  
 **Nvarchar (4000)**で公開される 15 の型のいずれかを指定する文字列、 **geometry**階層を入力します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 メソッドの入力は、次のいずれかにする必要があります: **Geometry**、**ポイント**、**曲線**、 **LineString**、 **CircularString**、 **CompoundCurve**、**画面**、**多角形**、 **CurvePolygon**、 **GeometryCollection**、 **MultiSurface**、 **MultiPolygon**、 **MultiCurve**、 **MultiLineString**、および**MultiPoint**です。 このメソッドはスロー、 **ArgumentException**と、入力の他の文字列が使用されます。  
  
## <a name="examples"></a>使用例  
 `MultiPoint` インスタンスを作成し、`InstanceOf()` を使用して、このインスタンスが `GeometryCollection` であるかどうかを判定する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

