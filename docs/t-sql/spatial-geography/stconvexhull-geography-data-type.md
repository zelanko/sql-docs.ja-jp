---
title: "STConvexHull (geography データ型) |Microsoft ドキュメント"
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
dev_langs: TSQL
helpviewer_keywords: STConvexHull method (geography)
ms.assetid: fb435db7-31bb-4243-9d8b-35379184cfb4
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e15e964e5f2f45b79fb6da569587185e5e468dc9
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="stconvexhull-geography-data-type"></a>STConvexHull (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  凸包を表すオブジェクトを返します、 **geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 返します、`FullGlobe`オブジェクトに対する**geography**がエンベロープの角度が 90 度より大きいインスタンス。  
  
 空白を返します**geography** 、空のコレクション**geography**インスタンス。  
  
 返します**null** 、初期化されていない**geography**インスタンス。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-stconvexhull-on-an-uninitialized-geography-instance"></a>A. 初期化されていない geography インスタンスに STConvexHull() を使用する  
 次の例で`STConvexHull()`、初期化されていない**geography**インスタンス。  
  
```
 DECLARE @g geography;  
 SELECT @g.STConvexHull();
 ```  
  
### <a name="b-using-stconvexhull-on-an-empty-geography-instance"></a>B. 空の geography インスタンスに STConvexHull を使用する  
 次の例で`STConvexHull()`、空で`Polygon`インスタンス。  
  
```
 DECLARE @g geography = 'POLYGON EMPTY';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
### <a name="c-finding-the-convex-hull-of-a-non-convex-polygon-instance"></a>C. 凸のない Polygon インスタンスの凸包を見つける  
 次の例で`STConvexHull()`を凸のないの凸包を見つける`Polygon`インスタンス。  
  
```  
 DECLARE @g geography;  
 SET @g = geography::Parse('POLYGON((-120.533 46.566, -118.283 46.1, -122.3 47.45, -120.533 46.566))');  
 SELECT @g.STConvexHull().ToString();  
```  
  
### <a name="d-finding-the-convex-hull-on-a-geography-instance-with-an-envelope-angle-larger-than-90-degrees"></a>D. エンベロープの角度が 90 度より大きい geography インスタンスで凸包を見つける  
 次の例で`STConvexHull()`上、 **geography**エンベロープの角度が 90 度より大きいインスタンス。  
  
```
 DECLARE @g geography = 'POLYGON((20.533 46.566, -18.283 46.1, -22.3 47.45, 20.533 46.566))';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
  
