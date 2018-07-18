---
title: STAsText (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STAsText (geography Data Type)
- STAsText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STAsText method
ms.assetid: d3d2635d-ca6c-4205-9d6c-eb939ee314fd
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 66f97709c3e8e639b7d32feae0cd4e34dedc36e3
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36242434"
---
# <a name="stastext-geography-data-type"></a>STAsText (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **geography** インスタンスの Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現を返します。 このテキストは、インスタンスに格納されている Z (標高) 値または M (メジャー) 値を含みません。  
  
 この **geography** データ型メソッドは、半球より大きい **FullGlobe** インスタンスまたは空間インスタンスをサポートします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **nvarchar(max)**  
  
 CLR の戻り値の型: **SqlChars**  
  
## <a name="remarks"></a>Remarks  
 **geography** インスタンスの OGC 型は、[STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md) を呼び出すことによって判別できます。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、サーバー上で返される結果セットが **FullGlobe** インスタンスに拡張されています。  
  
## <a name="examples"></a>使用例  
 `STAsText()` を使用して、`LineString``geography` インスタンスを、テキストから (-122.360, 47.656) ～ (-122.343, 47.656) の範囲で作成する例を次に示します。 その後、結果をテキストで返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
