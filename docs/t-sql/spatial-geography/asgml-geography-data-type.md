---
title: "AsGml (geography データ型) | Microsoft Docs"
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
- AsGml_(geography_Data_Type)_TSQL
- AsGml
- AsGml_TSQL
- AsGml (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- AsGml method
ms.assetid: 67795c64-d8d3-48dc-93ef-3c8a9274deb6
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4fe914c8f6f9d6a7547e36910be78878a66f19b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
#  <a name="asgml---geography-data-type"></a>AsGml - geography データ型
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **geography** インスタンスの Geography Markup Language (GML) 表現を返します。  
  
 GML (Geography Markup Language) の詳細については、Open Geospatial Consortium (OGC) の仕様書「[OGC の仕様、Geography Markup Language](http://go.microsoft.com/fwlink/?LinkId=93629)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
.AsGml ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **xml**  
  
 CLR 戻り値の型: **SqlXml**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>使用例  
 `LineString` インスタンスを作成し、`AsGML()` を使用して、インスタンスの GML 表現を返す例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.AsGml();  
```  
  
 このメソッドは、GML 表現を `LineString` インスタンスとして返します。  
  
```  
<LineString xmlns="http://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
