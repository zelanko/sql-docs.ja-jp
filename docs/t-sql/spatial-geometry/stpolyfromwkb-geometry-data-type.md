---
title: STPolyFromWKB (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPolyFromWKB_TSQL
- STPolyFromWKB (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPolyFromWKB (geometry Data Type)
ms.assetid: 8e8f0c41-0c62-4919-9d4c-d37c93fdd31c
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: cd9e5f6fe32a3a7652a87f9ff6fe5edf849b06e0
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65938295"
---
# <a name="stpolyfromwkb-geometry-data-type"></a>STPolyFromWKB (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Open Geospatial Consortium (OGC) Well-Known Binary (WKB) 表現を基に **geometryPolygon** インスタンスを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
STPolyFromWKB ( 'WKB_polygon' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *WKB_polygon*  
 返される **geometryPolygon** インスタンスの WKB 表現です。 *WKB_polygon* は、**varbinary (max)** 式です。  
  
 *SRID*  
 返される **geometryPolygon** インスタンスの SRID (spatial reference ID) を表す **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **geometry**  
  
 CLR の戻り値の型:**SqlGeometry**  
  
 OGC の型:**多角形**  
  
## <a name="remarks"></a>Remarks  
 このメソッドでは、入力が正しい形式でない場合に、**FormatException** をスローします。  
  
## <a name="examples"></a>使用例  
 `STPolyFromWKB()` を使用して `geometry` インスタンスを作成する例を次に示します。  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPolyFromWKB(0x0103000000010000000400000000000000000014400000000000001440000000000000244000000000000014400000000000002440000000000000244000000000000014400000000000001440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的なジオメトリ メソッド](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

