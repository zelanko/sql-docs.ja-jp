---
title: "STDimension (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDimension_TSQL
- STDimension (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDimension (geometry Data Type)
ms.assetid: 4fbd27dd-317b-4916-a8ae-4df1b8a6f27c
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 35e8b1b731fc9d557fa233adced67bdd76d0da09
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stdimension-geometry-data-type"></a>STDimension (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

最大次元数を返す、 **geometry**インスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **int**  
  
 CLR の戻り値の型: **SqlInt32**  
  
## <a name="remarks"></a>解説  
 `STDimension()`場合は-1 を返します、 **geometry**インスタンスが空です。  
  
## <a name="examples"></a>使用例  
 次の例を保持するテーブル変数を作成する**geometry**をインスタンス化し、挿入、 `Point`、 `LineString`、および`Polygon`です。  使用して、`STDimension()`をそれぞれのディメンションを返す**geometry**インスタンス。  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geometry);  
INSERT INTO @temp values ('Point', geometry::STGeomFromText('POINT(3 3)', 0));  
INSERT INTO @temp values ('LineString', geometry::STGeomFromText('LINESTRING(0 0, 3 3)', 0));  
INSERT INTO @temp values ('Polygon', geometry::STGeomFromText('POLYGON((0 0, 3 0, 0 3, 0 0))', 0));  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 この例では、それぞれのディメンション、返されます`geometry`インスタンス。  
  
|name|dim|  
|----------|---------|  
|ポイント|0|  
|LineString|1|  
|多角形|2|  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


