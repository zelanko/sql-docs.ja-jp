---
title: "STWithin (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
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
- STWithin_TSQL
- STWithin (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STWithin (geometry Data Type)
ms.assetid: f845d28c-8029-4e2b-bcf0-71c52a592501
caps.latest.revision: "25"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa8935b7f67d593be8a1246bbc035e1f8d6c520a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="stwithin-geometry-data-type"></a>STWithin (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

場合 1 を返します、 **geometry**インスタンスが別内では完全に**geometry**インスタンスです。 それ以外の場合は 0 を返します。 `STWithin`コマンドは、大文字小文字を区別します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STWithin ( other_geometry )  
```  
  
## <a name="arguments"></a>引数  
 *other_geometry*  
 もう 1 つ**geometry**対象のインスタンスと比較するインスタンス`STWithin()`が呼び出されます。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 このメソッドは、場合常に null を返しますの spatial reference Id (Srid)、 **geometry**インスタンスが一致しません。
  
## <a name="examples"></a>使用例  
 次の例で`STWithin()`2 つのテストに`geometry`インスタンスのかどうか、2 番目のインスタンス内で最初のインスタンスが完全にを参照してください。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STWithin(@h);  
```  
  
## <a name="see-also"></a>参照  
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

