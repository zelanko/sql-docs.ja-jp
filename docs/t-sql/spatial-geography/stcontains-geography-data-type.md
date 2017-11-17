---
title: "STContains (geography データ型) |Microsoft ドキュメント"
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
- STContains method (geography)
ms.assetid: b10e8f0a-2926-449a-82ea-be42543420ca
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 83927a3612c66d4c3bd84f67f4a2ca6940e9c9ef
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stcontains--geography-data-type"></a>STContains (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  指定するかどうか、呼び出し元**geography**インスタンスが空間的に含まれている、 **geography**インスタンス メソッドに渡されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STContains ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 もう 1 つ**geography**対象のインスタンスと比較するインスタンス`STContains()`が呼び出されます。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 場合 1 を返します、呼び出し元**geography**インスタンスが空間的に含まれている、 **geography**インスタンスは、メソッドに渡され、そうでない場合は 0 を返します。 返します**null**場合、2 つの SRID **geography**インスタンスが同じではありません。  
  
## <a name="examples"></a>使用例  
 次の例で`STContains()`2 つのテストに`geography`最初のインスタンスに 2 番目のインスタンスが含まれているかどうか。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SET @h = geography::Parse('POINT(-121.703796 46.893985)');  
```  
  
 `SELECT @g.STContains(@h);`  
  
  

