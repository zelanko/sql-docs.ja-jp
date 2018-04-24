---
title: STIsValid (geometry データ型) | Microsoft Docs
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
- STIsValid (geometry Data Type)
- STIsValid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsValid (geometry Data Type)
ms.assetid: 6da39bea-0f67-4660-98fc-d7214f9b2138
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f44318ffc62bfb38c78cd8fed74d403ff77ca7b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="stisvalid-geometry-data-type"></a>STIsValid (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Open Geospatial Consortium (OGC) の型に基づいて **geometry** インスタンスが整形式になっている場合は、true を返します。 **geometry** インスタンスが整形式になっていない場合は false を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **bit**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 **geometry** インスタンスの OGC 型は、[STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md) を呼び出すことによって判別できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、有効な **geometry** インスタンスのみを生成しますが、無効なインスタンスの取得と格納が可能です。 無効なインスタンスと同じ地点のセットを表す有効なインスタンスは、`MakeValid()` メソッドを使用して取得できます。  
  
## <a name="examples"></a>使用例  
 `geometry` インスタンスを作成し、`STIsValid()` を使用してこのインスタンスが有効かどうかをテストする例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsValid();  
```  
  
## <a name="see-also"></a>参照  
 [STGeometryType &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [MakeValid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

