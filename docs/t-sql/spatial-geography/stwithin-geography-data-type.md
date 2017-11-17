---
title: "STWithin (geography データ型) |Microsoft ドキュメント"
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
- STWithin method (geography)
ms.assetid: 6fc745cc-7976-418a-a89a-c267e64ab3a2
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c0347f3ceb94b52aab11378dbb058dd49b60e7b1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stwithin-geography-data-type"></a>STWithin (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  場合 1 を返します、 **geography**インスタンスが別内に空間的に**geography**インスタンスです。 それ以外の場合は 0 を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STWithin ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 もう 1 つ**geography**対象のインスタンスと比較するインスタンス`STWithin()`が呼び出されます。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 このメソッドは、場合常に null を返しますの spatial reference Id (Srid)、 **geography**インスタンスが一致しません。  
  
## <a name="examples"></a>使用例  
 次の例で`STWithin()`2 つのテストに`geography`インスタンスのかどうか、2 番目のインスタンス内で最初のインスタンスが完全にを参照してください。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('POLYGON ((-120.533 46.566, -118.283 46.1, -122.3 47.45, -120.533 46.566))');  
SET @h = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523), CIRCULARSTRING (-119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SELECT @g.STWithin(@h);  
```  
  
  

