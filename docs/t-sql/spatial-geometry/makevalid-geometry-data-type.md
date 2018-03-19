---
title: "MakeValid (geometry データ型) | Microsoft Docs"
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
- MakeValid
- MakeValid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MakeValid (geometry Data Type)
ms.assetid: 38673010-ab77-4ebb-9c4d-b26b79e3b7ea
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0694b49b23d87d30e7134c822de295ec5b840544
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="makevalid-geometry-data-type"></a>MakeValid (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

無効な **geometry** インスタンスを有効な Open Geospatial Consortium (OGC) 型の **geometry** インスタンスに変換します。
  
## <a name="syntax"></a>構文  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geometry**  
  
 CLR 戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 このメソッドにより、**geometry** インスタンスの型が変更されるだけでなく、**geometry** インスタンスの地点がわずかに移動する場合があります。  
  
## <a name="examples"></a>使用例  
 最初に、そのインスタンス自体が重なる、無効な `LineString` インスタンスを作成し、`STIsValid()` を使用して、無効なインスタンスであることを確認する例を示します。 `STIsValid()` は、無効なインスタンスに対して値 0 を返します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 0);  
SELECT @g.STIsValid();  
```  
  
 次に、`MakeValid()` を使用してインスタンスを有効にし、そのインスタンスが実際に有効であるかどうかをテストする例を示します。 `STIsValid()` は、有効なインスタンスに対して値 1 を返します。  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 最後に、このインスタンスがどのようにして有効なインスタンスに変換されたかを検証する例を示します。  
  
```  
SELECT @g.ToString();  
```  
  
 この例では、`LineString` インスタンスが選択されると、値は有効な `MultiLineString` インスタンスとして返されます。  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
 次の例では、CircularString インスタンスを Point インスタンスに変換します。  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 1 1, 1 1)';  
SELECT @g.MakeValid().ToString();  
```  
  
## <a name="see-also"></a>参照  
 [STIsValid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

