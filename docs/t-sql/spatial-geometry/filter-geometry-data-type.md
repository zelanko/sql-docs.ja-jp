---
title: "フィルター (geometry データ型) |Microsoft ドキュメント"
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
- Filter
- Filter_TSQL
- Filter (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: Filter method
ms.assetid: 3d629a39-157e-4159-a3ca-a3c2e0ed4160
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e09f4ac5d6d4ecaf32f6b500aee9a3a50c772c02
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="filter-geometry-data-type"></a>Filter (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

かどうかを高速のインデックス専用積集合メソッドを提供するメソッド、 **geometry**インスタンスでは、他と交差する**geometry**インスタンス、インデックスがあると仮定するとします。
  
場合 1 を返します、 **geometry**インスタンス可能性のある他と交差する**geometry**インスタンス。 このメソッドが false な正の値の戻り値を生成可能性があり、正確な結果のプランに依存する可能性があります。 共通部分がない場合、正確な 0 値 (真陰性の戻り値) を返します**geometry**インスタンスが見つかりませんでした。
  
インデックスが使用できない場合、または、実行されていない場合、メソッドと同じ値を返します**STIntersects()**同じパラメーターで呼び出されるとします。
  
## <a name="syntax"></a>構文  
  
```  
  
.Filter ( other_geometry )  
```  
  
## <a name="arguments"></a>引数  
 *other_geometry*  
 もう 1 つ**geometry**呼び出す。 が呼び出されるインスタンスと比較するインスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 このメソッドは決定的でなく、正確ではありません。  
  
## <a name="examples"></a>使用例  
 次の例で`Filter()`2 どうかを判断`geometry`互いに交差するインスタンス。  
  
```  
CREATE TABLE sample (id int primary key, g geometry);  
GO  
INSERT INTO sample VALUES  
   (0, geometry::Point(0, 0, 0)),  
   (1, geometry::Point(0, 1, 0)),  
   (2, geometry::Point(0, 2, 0)),  
   (3, geometry::Point(0, 3, 0)),  
   (4, geometry::Point(0, 4, 0));  
  
CREATE SPATIAL INDEX sample_idx ON sample(g)  
WITH (bounding_box = (-8000, -8000, 8000, 8000));  
GO  
SELECT id  
FROM sample   
WHERE g.Filter(geometry::Parse('POLYGON((-1 -1, 1 -1, 1 1, -1 1, -1 -1))')) = 1;  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [STIntersects &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
  

