---
title: "STDifference (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a4a5f767f3719f512bf0ff98545d135a65b4b5e
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="stdifference-geography-data-type"></a>STDifference (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  地点のセットを 1 つを表すオブジェクトを返します**geography**インスタンス別の外部にある**geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 もう 1 つ**geography**を示すインスタンス STDifference() が呼び出されるインスタンスから削除します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="exceptions"></a>例外  
 このメソッドは、 **ArgumentException**場合は、インスタンスに対蹠が含まれています。  
  
## <a name="remarks"></a>解説  
 このメソッドは、場合常に null を返しますの spatial reference identifier (Srid)、 **geography**インスタンスが一致しません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、サーバー上で返される結果セットが拡張されて**FullGlobe**インスタンス。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]半球より大きい空間インスタンスをサポートしています。 結果に円弧が含まれるのは、入力インスタンスに円弧が含まれる場合のみです。 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. 2 つの geography インスタンス間の差異を計算する  
 次の例で`STDifference()`2 つの差を計算する**geography**インスタンス。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-using-a-fullglobe-with-stdifference"></a>B. STDifference() と共に FullGlobe を使用する  
 `FullGlobe` インスタンスを使用する例を次に示します。 最初の結果は、空`GeometryCollection`され、2 つ目の結果は、`Polygon`インスタンス。 `STDifference()`空白を返します`GeometryCollection`ときに、`FullGlobe`インスタンスがパラメーター。 呼び出し元のすべてのポイント`geography`にインスタンスが含まれている、`FullGlobe`インスタンス。  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 DECLARE @h geography = 'FULLGLOBE';  
 SELECT @g.STDifference(@h).ToString(),  
 @h.STDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
