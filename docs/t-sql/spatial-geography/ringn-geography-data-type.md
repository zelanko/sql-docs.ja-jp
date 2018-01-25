---
title: "RingN (geography データ型) |Microsoft ドキュメント"
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
- RingN
- RingN_TSQL
dev_langs: TSQL
helpviewer_keywords: RingN method
ms.assetid: 30f47275-2727-4d22-bbec-c0c54bcb3ac2
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e08cc4d2a3359362b0e5bff28c2e18459863b120
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="ringn-geography-data-type"></a>RingN (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定したリングを返す、 **geography**インスタンス:`1 ≤ n ≤ NumRings()`です。  
  
## <a name="syntax"></a>構文  
  
```  
  
.RingN (expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 **Int** 1 ~ 内のリングの数の式、**多角形**インスタンス。  
  
## <a name="return-value"></a>戻り値  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 場合リング インデックスの値を **n**  1 未満の値は、このメソッドは、 **ArgumentOutOfRangeException です。** リング インデックス値は、1 以上、かつ `NumRings()` で返される数値以下である必要があります。  
  
## <a name="examples"></a>使用例  
 この例で作成、 `Polygon` 2 つのインスタンスのリングし、2 つ目のリングを返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.RingN(2).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [NumRings &#40;geography データ型&#41;](../../t-sql/spatial-geography/numrings-geography-data-type.md)  
  
  
