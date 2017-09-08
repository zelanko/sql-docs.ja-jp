---
title: "Z (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad6d857cb2028c34e6c1d1e9200537fbcd007989
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="z-geometry-data-type"></a>Z (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

インスタンスの Z (標高) 値です。 標高値のセマンティクスはユーザーが定義します。
  
## <a name="syntax"></a>構文  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型: **float**  
  
 CLR 型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 このプロパティの値は、geometry インスタンスがない場合、ポイントは null になりますと**ポイント**が設定されていないためインスタンス化します。  
  
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
 [M (&) #40";"geometry データ型"&"#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [AsTextZM (&) #40";"geometry データ型"&"#41;](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)   
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


