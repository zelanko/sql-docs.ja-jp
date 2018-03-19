---
title: "STGeomCollFromWKB (geometry データ型) | Microsoft Docs"
ms.custom: 
ms.date: 08/03/2017
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
- STGeomCollFromWKB (geometry Data Type)
- STGeomCollFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromWKB (geometry Data Type)
ms.assetid: 6c55032c-7f5e-4181-8e67-c0265032db63
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87203352667ccca98f440a136cd12917c64b48ad
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stgeomcollfromwkb-geometry-data-type"></a>STGeomCollFromWKB (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現を基に **geometrycollection** インスタンスを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
STGeomCollFromWKB ( 'WKB_geometrycollection' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *WKB_geometrycollection*  
 返される **geometrycollection** インスタンスの WKB 表現です。 *WKB_geometrycollection* は、**varbinary (max)** 式です。  
  
 *SRID*  
 返される **geometry** インスタンスの SRID (spatial reference ID) を表す **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geometry**  
  
 CLR 戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 `STGeomCollFromWKB()` によって返される **geometry** インスタンスの OGC 型は、対応する WKB 入力に基づき、**GeomCollection**、**MultiPolygon**、**MultiLineString**、**MulitPoint** のいずれかに設定されます。  
  
 このメソッドは、入力が適切な形式でない場合に、FormatException 例外をスローします。  
  
## <a name="examples"></a>使用例  
 `STGeomCollFromWKB()` を使用して **geometry** インスタンスを作成する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromWKB(0x0107000000020000000103000000010000000400000000000000000014400000000000001440000000000000244000000000000014400000000000002440000000000000244000000000000014400000000000001440010100000000000000000024400000000000002440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的なジオメトリ メソッド](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

