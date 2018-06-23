---
title: MultiPoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0106449b66e1f4c55edd28abfd4e2fab67626080
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175127"
---
# <a name="multipoint"></a>MultiPoint
  A `MultiPoint` 0 個以上のポイントのコレクションです。 `MultiPoint` インスタンスの境界は空になります。  
  
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
 [ポイント](point.md)   
 [空間データ &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  