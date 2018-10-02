---
title: STDistance (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance (geometry Data Type)
ms.assetid: ac815bc7-5342-4cc4-af40-c80a1c4c8b68
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6a983ca188da201bf18e407eaf3a84328a7abf29
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596052"
---
# <a name="stdistance-geometry-data-type"></a>STDistance (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  任意の **geometry** インスタンスの地点と別の **geometry** インスタンスの地点との最短距離を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STDistance ( other_geometry )  
```  
  
## <a name="arguments"></a>引数  
 *other_geometry*  
 `STDistance()` を呼び出したインスタンスまでの距離が測定される、別の **geometry** インスタンスです。 *other_geometry* が空のセットである場合、`STDistance()` は NULL を返します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **float**  
  
 CLR の戻り値の型: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 **geometry** インスタンスの SRID (spatial reference ID) が一致しない場合、`STDistance()` は常に null を返します。  
  
## <a name="examples"></a>使用例  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POINT(10 10)', 0);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>参照  
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
