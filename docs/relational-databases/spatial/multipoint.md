---
title: MultiPoint | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: spatial
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a88fe4695cf9de09cbd9b43ae9fd476508fb46fe
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="multipoint"></a>MultiPoint
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] **MultiPoint** は、0 個以上のポイントのコレクションです。 **MultiPoint** インスタンスの境界は空になります。  
  
## <a name="examples"></a>使用例  
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
  
 次のコード例では、 `STGeometryN()` メソッドを使用して、コレクション内の最初のポイントの説明を取得します。  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a>参照  
 [ポイント](../../relational-databases/spatial/point.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
