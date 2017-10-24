---
title: "MakeValid (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- MakeValid method (geography)
ms.assetid: f67038e3-4f62-4465-994e-e95ac27d8ada
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ca7928d73b20bfa024466cc580b1958c250c9d8e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="makevalid-geography-data-type"></a>MakeValid (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  変換、 **geography**を有効な無効なインスタンス**geography**有効な Open Geospatial Consortium (OGC) 型のインスタンス。  
  
 入力オブジェクト STIsValid()、False を返す場合`MakeValid()`が有効なインスタンスに無効なインスタンスに変換します。  
  
 この geography データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 このメソッドの型を変更する可能性があります、 **geography**インスタンス。 さらのポイント、 **geography**インスタンスわずかに移動することがあります。 NumPoint() など一部のメソッドから結果が変わる可能性があります。  
  
 無効な空間インスタンスが赤道と交差して、EnvelopeAngle() が場合 = 180 で、 **FullGlobe**インスタンスが返されます。 `MakeValid()` **Geography**データ型のメソッドは有効なインスタンスを返すように最善の試みになりますが、結果が正確であるとは限りません。  
  
> [!NOTE]  
>  無効なオブジェクトをデータベースに格納することができます。 無効なインスタンスで実行できるメソッドは、有効性を確認またはエクスポートを許可するメソッドを (どの STIsValid() のそれらのインスタンスは False を返します)。 STIsValid()、MakeValid()、:stastext()、STAsBinary()、ToString()、AsTextZM()、および AsGml() です。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
 最初の例では、無効な`LineString`自体が重なるし、使用するインスタンス`STIsValid()`無効なインスタンスであることを確認します。 `STIsValid()`無効なインスタンスの場合は 0 の値を返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 4326);  
SELECT @g.STIsValid();  
```  
  
 2 番目の例では`MakeValid()`インスタンスを有効にするため、インスタンスが実際に有効であるかをテストします。 `STIsValid()`有効なインスタンスの 1 の値を返します。  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 最後に、このインスタンスがどのようにして有効なインスタンスに変換されたかを検証する例を示します。  
  
```  
SELECT @g.ToString();  
```  
  
 この例では、ときに、`LineString`インスタンスが選択されている、値を返す有効なと`MultiLineString`インスタンス。  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
## <a name="see-also"></a>参照  
 [STIsValid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

