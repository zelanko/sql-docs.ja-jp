---
title: "STLength (geometry データ型) |Microsoft ドキュメント"
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
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9eacaffeb5998152e5a87f4cf058aa7374076a92
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stlength-geometry-data-type"></a>STLength (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

内の要素の長さの合計を返します、 **geometry**インスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **float**  
  
 CLR の戻り値の型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 場合、 **geometry**インスタンスが閉じて、その長さはインスタンスの周囲の合計長として計算です。 多角形の長さが周囲および地点の長さは 0 です。 任意の長さ**geometrycollection**型に含まれるの長さの合計は**geometry**インスタンス。  
  
 STLength() は、LineString が有効でも無効でも動作します。 通常、LineString が無効になるのは、線分の重複のためです。これは、不正確な GPS のトレースなどの異常によって起きる場合があります。 STLength() は、重複する線分や無効な線分を削除しません。 返される長さの値には、重複する線分や無効な線分が含まれています。 MakeValid() メソッドは、LineString から重複する線分を削除できます。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`LineString`使用して、インスタンス`STLength()`インスタンスの長さが見つかりません。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


