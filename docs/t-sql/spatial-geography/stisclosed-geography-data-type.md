---
title: "STIsClosed (geography データ型) |Microsoft ドキュメント"
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
- STIsClosed (geography Data Type)
- STIsClosed_TSQL
dev_langs: TSQL
helpviewer_keywords: STIsClosed method
ms.assetid: eba1643f-07c4-4500-8643-b7e90f908147
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 707a7b289874bb4181d660cb63ab399cd4cdd11d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="stisclosed-geography-data-type"></a>STIsClosed (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  場合 1 を返します、始点と終点の指定された**geography**が同じをインスタンス化します。 1 を返します**geography**コレクション型の場合、含まれている各**geography**インスタンスが閉じています。 インスタンスが閉じていない場合は 0 を返します。  
  
 これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 このメソッドが存在する場合、0 を返しますの図形、 **geography**インスタンスが、ポイント、か、インスタンスが空です。  
  
 場合に、このメソッドが true を返します、 **FullGlobe**インスタンスが、**多角形**などその他の型のインスタンス。  
  
 すべて**多角形**インスタンスが閉じられたと見なされます。  
  
## <a name="examples"></a>使用例  
 `Polygon` インスタンスを作成し、`STIsClosed()` を使用して `Polygon` が閉じているかどうかをテストする例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
