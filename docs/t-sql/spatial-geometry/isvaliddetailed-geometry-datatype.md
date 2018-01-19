---
title: "IsValidDetailed (geometry データ型) |Microsoft ドキュメント"
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
dev_langs: TSQL
helpviewer_keywords: IsValidDetailed geometry
ms.assetid: 5a31e88a-ad7b-4ef7-b773-e2571f1cb3aa
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddffd6c929bdf5ce13a05ceee6ce27fc1b06b3c5
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="isvaliddetailed-geometry-datatype"></a>IsValidDetailed (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

無効な空間オブジェクトの問題の特定に役立つメッセージを返します。 オブジェクトが無効な場合は、最初のエラーだけが返されます。 オブジェクトが有効な場合は、値 24400 が返されます。
  
## <a name="syntax"></a>構文  
  
```  
  
.IsValidDetailed()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] return type: **nvarchar(max)**  
  
 CLR の戻り値の型:**文字列**  
  
## <a name="remarks"></a>解説  
 次の表に、返される可能性のある戻り値を示します。  
  
|戻り値|Description|  
|------------------|-----------------|  
|24400|有効です|  
|24401|無効です。原因は不明です。|  
|24402|ポイント {0} がこの型のオブジェクトで無効な孤立点であるため無効です。|  
|24403|多角形のエッジの一部のペアが重なり合っているため無効です。|  
|24404|多角形のリング {0} がそのリング自体または別のリングと交差しているため無効です|  
|24405|一部の多角形のリングがそのリング自体または別のリングと交差しているため無効です。|  
|24406|曲線 {0} が 1 点に退化しているため無効です。|  
|24407|多角形のリング {0} がポイント {1} 一度に 1 行を折りたたむため無効です。|  
|24408|多角形のリング {0} が閉じていないため無効です。|  
|24409|多角形のリング {0} の一部が多角形の内部に存在するため無効です。|  
|24410|リング {0} が外部リングではない多角形の最初のリングのため無効です。|  
|24411|リング {0} が多角形の外部リング {1} 外にあるため無効です。|  
|24412|リング {0} と {1} 多角形の内部が接続されていないため無効です。|  
|24413|曲線 {0} の 2 つのエッジが重なり合っているため無効です。|  
|24414|曲線 {0} のエッジには 1 曲線 \} のエッジが重なっているため無効です。|  
|24415|一部の多角形が無効なリング構造になっているため無効です。|  
|24416|曲線 {0} 時点で開始するエッジ {1} は直線または対蹠エンドポイントを含む逆円弧であるため無効です。|  
  
## <a name="examples"></a>使用例  
 無効な空間オブジェクトの次の例を示していますが、どのように**IsValidDetailed()**メソッドの動作です。  
  
```sql  
DECLARE @p GEOMETRY = 'Polygon((2 2, 4 4, 4 2, 2 4, 2 2))'  
SELECT @p.IsValidDetailed()  
--Returns: 24404: Not valid because polygon ring (1) intersects itself or some other ring.  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

