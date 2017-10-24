---
title: "Z (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Z (geography Data Type)
- Z_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z method
ms.assetid: 9abc79c5-43c9-4cc2-b37f-d2ecdec7c234
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f185da3a7aeabb751f0d871d6ad2c0132830d9d7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="z-geography-data-type"></a>Z (geography データ型)
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
 このプロパティの値が null 場合、 **geography**インスタンスが、ポイントではないと**ポイント**インスタンスの場合、これが設定されていません。  
  
 このプロパティは読み取り専用です。  
  
 Z 座標はライブラリが行う計算では使用されません。また、ライブラリが行う計算によって渡されることもありません。  
  
## <a name="examples"></a>使用例  
 次の例では、Z (標高) 値と M (メジャー) 値を含む `Point` インスタンスを作成し、`Z` を使用してインスタンスの Z 値をフェッチします。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M (&) #40";"geography データ型"&"#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [AsTextZM &#40;geography データ型&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  

