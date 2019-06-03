---
title: STNumPoints (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumPoints_TSQL
- STNumPoints (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STNumPoints (geometry Data Type)
ms.assetid: a19520fc-7f91-4a2c-856f-4d8b99a7e496
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 1eb97aa0ec64552049a33f9483beb5318a39ff48
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65938498"
---
# <a name="stnumpoints-geometry-data-type"></a>STNumPoints (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  **geometry** インスタンス内の各図形に含まれる地点の合計数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STNumPoints ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **int**  
  
 CLR の戻り値の型:**SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、**geometry** インスタンスの記述に含まれている地点をカウントします。 重複する地点はカウントされます。 このインスタンスが**コレクション**型の場合、このメソッドは各要素内の地点の合計数を返します。  
  
## <a name="examples"></a>使用例  
 `LineString` インスタンスを作成し、`STNumPoints()` を使用して、インスタンスの記述で使用されている地点の数を確認する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STNumPoints();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
