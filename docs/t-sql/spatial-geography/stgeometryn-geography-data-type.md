---
title: "STGeometryN (geography データ型) |Microsoft ドキュメント"
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
- STGeometryN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d5d11dc77ce692543068cba6739ef982bc8264c8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定したを返します**geography**内の要素、 **GeometryCollection**またはそのサブタイプのいずれか。 サブタイプで STGeometryN() を使用する場合、 **GeometryCollection**など**MultiPoint**または**MultiLineString**、このメソッドが戻る、 **geography** N = 1 で呼び出された場合をインスタンス化します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 **Int**式 1 ~ 数**geography**のインスタンスにある、 **GeometryCollection**です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 このメソッドは、パラメーターがの結果よりも大きい場合は null を返します[STNumGeometries()](../../t-sql/spatial-geography/stnumgeometries-geography-data-type.md)とスローされます、 **ArgumentOutOfRangeException**場合、*式*パラメーターは、1 より小さいです。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`MultiPoint``geography`使用して、インスタンス`STGeometryN()`をもう 1 つを検索する`geography`のインスタンス、 **GeometryCollection**です。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

