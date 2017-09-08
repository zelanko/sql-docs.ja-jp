---
title: "STNumPoints (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STNumPoints_TSQL
- STNumPoints (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STNumPoints (geometry Data Type)
ms.assetid: a19520fc-7f91-4a2c-856f-4d8b99a7e496
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17dc20837c72439fc79fec62170edfb8eca34d9a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stnumpoints-geometry-data-type"></a>STNumPoints (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  図形の各ポイントの数の合計を返して、 **geometry**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STNumPoints ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **int**  
  
 CLR の戻り値の型: **SqlInt32**  
  
## <a name="remarks"></a>解説  
 このメソッドの説明内のポイントの数、 **geometry**インスタンス。 重複する地点はカウントされます。 このインスタンスの場合、**コレクション**各要素の型では、このメソッドが戻るポイントの合計。  
  
## <a name="examples"></a>使用例  
 `LineString` インスタンスを作成し、`STNumPoints()` を使用して、インスタンスの記述で使用されている地点の数を確認する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STNumPoints();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

