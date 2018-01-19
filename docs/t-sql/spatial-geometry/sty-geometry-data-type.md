---
title: "STY (geometry データ型) |Microsoft ドキュメント"
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
- STY_TSQL
- STY (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STY (geometry Data Type)
ms.assetid: f72e0eaa-7d1d-4052-88fd-a172d8cb0d71
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1177c430db2dea25e9fbb26efed52fa0781bff3e
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="sty-geometry-data-type"></a>STY (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Y 座標プロパティ、**ポイント**インスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.STY  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型: **float**  
  
 CLR 型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 このプロパティの値が null にする場合、 **geometry**インスタンスが地点です。 このプロパティは読み取り専用です。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`Point`使用して、インスタンス`STY`をインスタンスの Y 座標を取得します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STY;  
```  
  
## <a name="see-also"></a>参照  
 [STX &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STSrid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

