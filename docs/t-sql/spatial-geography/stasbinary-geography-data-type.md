---
title: "STAsBinary (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STAsBinary_TSQL
- STAsBinary (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STAsBinary method
ms.assetid: 99602a62-265d-4aa4-a8dc-92992ca55ba4
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c48fc48b7af524e980801a11ac2574f2091823a2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stasbinary-geography-data-type"></a>STAsBinary (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Open Geospatial Consortium (OGC) Well-Known Binary (WKB) 表現を返します、 **geography**インスタンス。  
  
 これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STAsBinary ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **varbinary (max)**  
  
 CLR の戻り値の型: **SqlBytes**  
  
## <a name="remarks"></a>解説  
 OGC の型の**geography**インスタンスを呼び出すことによって判別できます[STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)です。  
  
## <a name="examples"></a>使用例  
 次の例で`STAsBinary()`を作成する、`LineString``geography`インスタンスから (-122.360, 47.656) に (-122.343, 47.656) テキストからです。 その後、結果を WKB で返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING( -122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsBinary();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

