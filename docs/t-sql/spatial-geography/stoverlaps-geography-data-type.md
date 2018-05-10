---
title: STOverlaps (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STOverlaps method (geography)
ms.assetid: 2babbb9c-59ef-4494-9e6b-528cf296cbd7
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1c387d178f4455eb863c6a08c7b80e50e598d512
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="stoverlaps-geography-data-type"></a>STOverlaps (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **geography** インスタンスが別の **geography** インスタンスと空間的に重複する場合は 1 を返します。それ以外の場合は 0 を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STOverlaps ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 `STOverlaps()` を呼び出したインスタンスと比較される、別の **geography** インスタンスです。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **bit**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 2 つの **geography** インスタンスの SRID (spatial reference ID) が一致しない場合、このメソッドは常に null を返します。  
  
## <a name="examples"></a>使用例  
 `STOverlaps()` を使用して 2 つの **geography** インスタンスが重なっているかどうかをテストする例を次に示します。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('POLYGON ((-120.533 46.566, -118.283 46.1, -122.3 47.45, -120.533 46.566))');  
SET @h = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523), CIRCULARSTRING (-119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SELECT @g.STOverlaps(@h);  
```  
  
  
