---
title: "Point (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point method
- Point (geography Data Type)
ms.assetid: 0dc6f422-7aae-4016-b7f4-3289fa8f989c
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cefb6e199bbd4617b1fc2f6f71d9bb3997445dc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="point-geography-data-type"></a>Point (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

構築、 **geography**インスタンスを表す、**ポイント**の緯度と経度の値から spatial reference ID (SRID) のインスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>引数  
 *Lat*  
 **Float**の x 座標を表す式、**ポイント**生成されています。  
  
 *長い*  
 **Float**の y 座標を表す式、**ポイント**生成されています。 有効な経度と緯度の値の詳細については、次を参照してください。[ポイント](../../relational-databases/spatial/point.md)です。  
  
 *SRID*  
 **Int**の SRID を表す式、 **geography**インスタンスを取得します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
> [!NOTE]  
>  Point (geography データ型) メソッドの引数は、WKT と比較して元に戻された座標を持ちます。  
  
## <a name="examples"></a>使用例  
 次の例で`Point()`を作成する、`geography`インスタンス。  
  
```  
DECLARE @g geography;   
SET @g = geography::Point(47.65100, -122.34900, 4326)  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [拡張された静的な地理メソッド](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

