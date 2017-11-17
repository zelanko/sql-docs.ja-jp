---
title: "STLength (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- STLength (geography Data Type)
- STLength_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLength method
ms.assetid: 774560ab-4a4a-4058-b043-1e67cf6fb9eb
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f7591a690723d0835916307f1bbb6cea94ec147
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stlength-geography-data-type"></a>STLength (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  内の要素の長さの合計を返します、 **geography**インスタンスまたは**geography**インスタンス内で、 **GeometryCollection**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **float**  
  
 CLR の戻り値の型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 場合、 **geography**インスタンスが閉じている、その長さはインスタンスの周囲の合計長として計算です。 多角形の長さが周囲、および地点の長さは 0 です。 長さ、 **GeometryCollection**のすべての長さの合計を計算することによって検出された、 **geography**インスタンスがコレクション内に存在します。  
  
 STLength() は、LineString が有効でも無効でも動作します。 通常、LineString が無効になるのは、線分の重複のためです。これは、不正確な GPS のトレースなどの異常によって起きる場合があります。 STLength() は、重複する線分や無効な線分を削除しません。 返される長さの値には、重複する線分や無効な線分が含まれています。 MakeValid() メソッドは、LineString から重複する線分を削除できます。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`LineString`使用して、インスタンス`STLength()`インスタンスの長さが見つかりません。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

