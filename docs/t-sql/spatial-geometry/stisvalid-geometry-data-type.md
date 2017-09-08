---
title: "STIsValid (geometry データ型) |Microsoft ドキュメント"
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
- STIsValid (geometry Data Type)
- STIsValid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsValid (geometry Data Type)
ms.assetid: 6da39bea-0f67-4660-98fc-d7214f9b2138
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3726790e2d4b5cfc235ca59f96e4247726161bf7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stisvalid-geometry-data-type"></a>STIsValid (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

場合は true を返します、 **geometry**インスタンスは、Open Geospatial Consortium (OGC) 型に基づいて、適切な形式です。 場合は false を返します、 **geometry**インスタンスが整形式ではありません。
  
## <a name="syntax"></a>構文  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 OGC の型の**geometry**インスタンスを呼び出すことによって判別できます[STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のみの有効な生成**geometry**インスタンスしますが、無効なインスタンスの取得と記憶域が可能です。 無効なインスタンスと同じ地点のセットを表す有効なインスタンスは、`MakeValid()` メソッドを使用して取得できます。  
  
## <a name="examples"></a>使用例  
 `geometry` インスタンスを作成し、`STIsValid()` を使用してこのインスタンスが有効かどうかをテストする例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsValid();  
```  
  
## <a name="see-also"></a>参照  
 [STGeometryType (&) #40";"geometry データ型"&"#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [MakeValid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


