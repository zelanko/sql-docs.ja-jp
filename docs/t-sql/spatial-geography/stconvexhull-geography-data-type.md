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
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull method (geography)
ms.assetid: fb435db7-31bb-4243-9d8b-35379184cfb4
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a8376d12352994cd768b806f5ce47463196d4bfd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
  
  

