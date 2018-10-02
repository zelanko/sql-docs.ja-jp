---
title: STStartPoint (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STStartPoint_TSQL
- STStartPoint (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STStartPoint (geometry Data Type)
ms.assetid: 049917db-3f76-4053-8cd2-bc54158e89bc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff24ccb799c4a0e4b199399a58c1df41c8a4c4bd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629100"
---
# <a name="ststartpoint-geometry-data-type"></a>STStartPoint (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry** インスタンスの始点を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STStartPoint ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **geometry**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC) の型: **Point**  
  
## <a name="remarks"></a>Remarks  
 `STStartPoint()` は、[STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md) (1) と同じです。  
  
## <a name="examples"></a>使用例  
 `LineString` インスタンスを作成し、`STStartPoint()` を使用してこのインスタンスの始点を取得する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0;  
SELECT @g.STStartPoint().ToString();  
```  
  
## <a name="see-also"></a>参照  
 [STPointN &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

