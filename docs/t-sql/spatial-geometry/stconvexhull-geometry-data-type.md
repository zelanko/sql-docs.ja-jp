---
title: STConvexHull (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STConvexHull (geometry Data Type)
- STConvexHull_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull (geometry Data Type)
ms.assetid: 60a520a6-1a7c-486b-8d91-34401edf6233
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: ba1d23e85d18215092768e41f7962516b3ff036a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748722"
---
# <a name="stconvexhull-geometry-data-type"></a>STConvexHull (geometry データ型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

**geometry** インスタンスの凸包を表すオブジェクトを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **geometry**  
  
 CLR 戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 `STConvexHull()` は、指定された **geometry** インスタンスを含む最小の凸多角形を返します。 **Points** インスタンスまたは同一直線上の **LineString** インスタンスは、入力と同じ型のインスタンスを作成します。  
  
## <a name="examples"></a>例  
 次の例では、`STConvexHull()` を使用して、凸のない `Polygon``geometry` インスタンスの凸包を見つけます。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 1 1, 2 2, 2 0, 0 0))', 0);  
SELECT @g.STConvexHull().ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

