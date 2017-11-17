---
title: "STArea (geography データ型) |Microsoft ドキュメント"
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
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e96ee94983746e162990b8eadad4f6affb4f92fd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="starea-geography-data-type"></a>STArea (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  合計面積を返します、 **geography**インスタンス。 STArea() の結果の空間参照識別子が使用する測定単位の平方で返されます、 **geography** ; のインスタンスなど、インスタンスの SRID が 4326 の場合は、STArea() 結果を返します平方メートル単位で。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **float**  
  
 CLR の戻り値の型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 STArea() は 0 を返します、 **geography**インスタンスには、0-1 次元の図形のみが含まれています。 空である場合またはします。  
  
> [!NOTE]  
>  メソッドを**geography**データ型の基準の戻り値は、メソッドで使用されるインスタンスの srid に応じて、異なる結果を生成します。 Srid の詳細については、次を参照してください。 [Spatial Reference Id & #40 です。Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>使用例  
 次の例で`STArea()`を作成する、`Polygon``geography`をインスタンス化し、多角形の面積を計算します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

