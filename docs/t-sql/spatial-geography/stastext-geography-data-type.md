---
title: "STAsText (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- STAsText (geography Data Type)
- STAsText_TSQL
dev_langs: TSQL
helpviewer_keywords: STAsText method
ms.assetid: d3d2635d-ca6c-4205-9d6c-eb939ee314fd
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 164809adbc58d2aef1d27168f5b775117a2634f1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="stastext-geography-data-type"></a>STAsText (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現を返します、 **geography**インスタンス。 このテキストは、インスタンスに格納されている Z (標高) 値または M (メジャー) 値を含みません。  
  
 これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **nvarchar (max)**  
  
 CLR の戻り値の型: **SqlChars**  
  
## <a name="remarks"></a>解説  
 OGC の型の**geography**インスタンスを呼び出すことによって判別できます[STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)です。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、サーバー上で返される結果セットが拡張されて**FullGlobe**インスタンス。  
  
## <a name="examples"></a>使用例  
 次の例で`STAsText()`を作成する、`LineString``geography`インスタンスから (-122.360, 47.656) に (-122.343, 47.656) テキストからです。 その後、結果をテキストで返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
