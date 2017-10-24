---
title: "STIsRing (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STIsRing_TSQL
- STIsRing (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsRing (geometry Data Type)
ms.assetid: ea0063be-1c74-4cc4-ac6f-b65321ddfa54
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3417f5da487ea7de5d7c51820316dae3caf8bb0e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stisring-geometry-data-type"></a>STIsRing (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

場合 1 を返します、 **geometry**インスタンスは、次の要件を満たします。
-   **LineString**インスタンス。  
-   閉じている。  
-   単純である。  
-   場合 0 を返します、 **LineString**インスタンスが要件を満たしていません。  

 **Geometry**が閉じていて、単純なインスタンス両方[STIsClosed()](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)と[STIsSimple()](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md)インスタンスで呼び出されたときに 1 を返す必要があります。 インスタンスの型を決定する、 **geometry**を使用して[STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STIsRing ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 このメソッドは、インスタンスがない場合は null を返します、 **LineString**です。  
  
## <a name="examples"></a>使用例  
 `LineString` インスタンスを作成し、`STIsRing()` を使用して、このインスタンスがリングかどうかをテストする例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0, 0 0)', 0);  
SELECT @g.STIsRing();  
```  
  
## <a name="see-also"></a>参照  
 [STIsClosed &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [STGeometryType (&) #40";"geometry データ型"&"#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [STIsSimple (&) #40";"geometry データ型"&"#41;](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


