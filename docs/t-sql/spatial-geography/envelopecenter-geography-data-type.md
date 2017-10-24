---
title: "EnvelopeCenter (geography データ型) |Microsoft ドキュメント"
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
- EnvelopeCenter
- EnvelopeCenter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeCenter method
ms.assetid: dee9d807-faad-45b8-b3f3-7e8aa7d07147
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0638e8793c75ad78aafa12bec1d1f8a3061022c2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="envelopecenter-geography-data-type-"></a>EnvelopeCenter (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  外接する円の中心として使用できる点を返します、 **geography**インスタンス。  
  
 外接する円を決めるため、インスタンスの各点が地球の中心から地表上の点へのベクトルとして記述されます。 外接する円の中心点は、すべてのベクトルの平均として計算されます。 閉じたループのどちらかに、**多角形**インスタンスまたは**linestring**インスタンス、最初と最後のポイントが 1 回だけ使用します。  
  
 これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
EnvelopeCenter( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 このメソッドが戻る、**ポイント**です。 使用すると`EnvelopeAngle()`、`EnvelopeCenter()`の外接する円を返します、 **geography**インスタンス。  
  
> [!NOTE]  
>  `EnvelopeCenter()`外接する円を返します、 **geography**最小の外接する円を生成するためには、インスタンスが、結果は保証はありません。 これに対し、 **geometry**データ型のメソッド`STEnvelope()`時に返される最小の境界ボックスに適用されていることが保証、 **geometry**インスタンス。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降では、された、このインスタンスのエンベロープを表す円の中心を返すと、**ポイント**です。 定義されているすべてのラージ オブジェクトの`EnvelopeAngle()`= 180 で`EnvelopeCenter()`(90, 0) が返されます。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';  
SELECT @g.EnvelopeCenter().ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeAngle (&) #40";"geography データ型"&"#41;](../../t-sql/spatial-geography/envelopeangle-geography-data-type.md)  
  
  

