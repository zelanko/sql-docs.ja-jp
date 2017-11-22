---
title: "フィルター (geography データ型) |Microsoft ドキュメント"
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
- Filter
- Filter_TSQL
- Filter (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: Filter method
ms.assetid: 82a8f54a-3a47-4e20-b13a-b148029c5448
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5d85017831deaef0a0aa0a57b96fb40618520d3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="filter-geography-data-type"></a>Filter (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  かどうかを高速のインデックス専用積集合メソッドを提供するメソッド、 **geography**インスタンスでは、他と交差する**geography**インスタンス、インデックスがあると仮定するとします。  
  
 場合 1 を返します、 **geography**インスタンス可能性のある他と交差する**geography**インスタンス。 このメソッドは偽陽性の戻り値を生成する場合があり、正確な結果はプランによって異なります。 共通部分がない場合、正確な 0 値 (真陰性の戻り値) を返します**geography**インスタンスが見つかりませんでした。  
  
 インデックスが使用できない場合、または、実行されていない場合、メソッドと同じ値を返します**STIntersects()**同じパラメーターで呼び出されるとします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.Filter ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 もう 1 つ**geography**呼び出す。 が呼び出されるインスタンスと比較するインスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 このメソッドは決定的でなく、正確ではありません。  
  
## <a name="examples"></a>使用例  
 次の例で`Filter()`2 どうかを判断`geography`互いに交差するインスタンス。  
  
```  
CREATE TABLE sample (id int primary key, g geography);  
INSERT INTO sample VALUES  
   (0, geography::Point(45, -120, 4326)),  
   (1, geography::Point(45, -120.1, 4326)),  
   (2, geography::Point(45, -120.2, 4326)),  
   (3, geography::Point(45, -120.3, 4326)),  
   (4, geography::Point(45, -120.4, 4326));  
  
CREATE SPATIAL INDEX sample_idx on sample(g);  
SELECT id  
FROM sample   
WHERE g.Filter(geography::Parse(  
   'POLYGON((-120.1 44.9, -119.9 44.9, -119.9 45.1, -120.1 45.1, -120.1 44.9))')) = 1;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [STIntersects &#40;geography データ型&#41;](../../t-sql/spatial-geography/stintersects-geography-data-type.md)  
  
  
