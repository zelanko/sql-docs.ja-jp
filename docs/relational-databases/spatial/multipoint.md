---
title: MultiPoint | Microsoft Docs
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1cf571df37585a4a3e575d03b8cc1cd905fdffd1
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018577"
---
# <a name="multipoint"></a>MultiPoint
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **MultiPoint** は、0 個以上のポイントのコレクションです。 **MultiPoint** インスタンスの境界は空になります。  
  
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
  
  
