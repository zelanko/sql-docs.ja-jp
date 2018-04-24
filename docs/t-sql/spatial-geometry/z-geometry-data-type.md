---
title: Z (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Z (geometry Data Type)
- Z_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z (geometry Data Type)
ms.assetid: a62ed736-44df-4591-9109-ce90e1df9bd3
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c774b2af91400d77f3b9f25b75b4f77fd97a3a4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="z-geometry-data-type"></a>Z (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

インスタンスの Z (標高) 値です。 標高値のセマンティクスはユーザーが定義します。
  
## <a name="syntax"></a>構文  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の型: **float**  
  
 CLR の型: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 geometry インスタンスが Point ではない場合や、**Point** インスタンスにこのプロパティの値が設定されていない場合は、このプロパティの値は null になります。  
  
 このプロパティは読み取り専用です。  
  
 Z 座標値はライブラリが行う計算では使用されません。また、ライブラリが行う計算によって渡されることもありません。  
  
## <a name="examples"></a>使用例  
 次の例では、Z (標高) 値と M (メジャー) 値を含む `Point` インスタンスを作成し、`Z` を使用してインスタンスの Z 値をフェッチします。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>参照  
 [M &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [AsTextZM &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)   
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

