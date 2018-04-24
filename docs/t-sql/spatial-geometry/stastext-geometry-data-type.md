---
title: STAsText (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 09910822e272aaedd5f7f713352c0da83b59a1b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="stastext-geometry-data-type"></a>STAsText (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

**geometry** インスタンスの Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現を返します。 このテキストは、インスタンスに格納されている Z (標高) 値または M (メジャー) 値を含みません。
  
## <a name="syntax"></a>構文  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **nvarchar(max)**  
  
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
  
  

