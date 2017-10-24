---
title: "STAsText (geometry データ型) |Microsoft ドキュメント"
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
- STAsText_TSQL
- STAsText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STAsText (geometry Data Type)
ms.assetid: e0decf5e-2858-4c56-b61a-6123f47fb51c
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 127e64908ad9cb768d31e3c1ec42988962289246
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stastext-geometry-data-type"></a>STAsText (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現を返します、 **geometry**インスタンス。 このテキストは、インスタンスに格納されている Z (標高) 値または M (メジャー) 値を含みません。
  
## <a name="syntax"></a>構文  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **nvarchar (max)**  
  
 CLR の戻り値の型: **SqlChars**  
  
## <a name="examples"></a>使用例  
 次の例では、(0,0) から (2,3) までの `LineString` geometry インスタンスをテキストから作成します。 `STAsText()` は結果をテキストで返します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 3)', 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


