---
title: "MultiPoint | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "geometry サブタイプ MultiPoint [SQL Server]"
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MultiPoint
  **MultiPoint** は、0 個以上のポイントのコレクションです。 **MultiPoint** インスタンスの境界は空になります。  
  
## 使用例  
 次の例では、SRID が 23 で、ポイントが 2 つある (1 つは座標 (2,3) のポイントで、もう 1 つは座標 (7,8) で Z が 9.5 のポイント) `geometry MultiPoint` インスタンスを作成します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 この `MultiPoint` インスタンスは、次のように `STMPointFromText()` を使用して表現することもできます。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 次のコード例では、`STGeometryN()` メソッドを使用して、コレクション内の最初のポイントの説明を取得します。  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## 参照  
 [ポイント](../../relational-databases/spatial/point.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  