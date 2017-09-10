---
title: "M (geography データ型) |Microsoft ドキュメント"
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
- M (geography Data Type)
- M_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- M method
ms.assetid: cdba04f0-4e17-48f6-bafb-b1f918c5a501
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9edb3d7c84fe1f92bb5888e97a782985d05ddd4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="m-geography-data-type"></a>M (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **M** (メジャー) 値、 **geography**インスタンス。 メジャー値のセマンティクスはユーザー自身が定義しますが、一般的には線分に沿った距離を指します。 たとえば、メジャー値を使用して、道路沿いのマイル標を追跡できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
.M  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型: **float**  
  
 CLR 型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 このプロパティの値が null 場合、 **geography**インスタンスではありません、**ポイント**,、およびこの**ポイント**が設定されていないためインスタンス化します。  
  
 このプロパティは読み取り専用です。  
  
 M 値は、ライブラリによる計算では使用されません。また、ライブラリによる計算によって渡されることもありません。  
  
## <a name="examples"></a>使用例  
 次の例では、Z (標高) 値と M (メジャー) 値を含む `Point` インスタンスを作成し、`M` を使用してインスタンスの `M` 値をフェッチします。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.M;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [Z & #40";"geography データ型"&"#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
