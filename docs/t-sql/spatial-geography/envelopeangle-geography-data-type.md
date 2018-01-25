---
title: "EnvelopeAngle (geography データ型) |Microsoft ドキュメント"
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
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs: TSQL
helpviewer_keywords: EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 692287aee372bf349cfa795e3b52c6e84c8e4f42
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  によって返されるポイント間の最大角度を返します`EnvelopeCenter()`と特定の時点に、 **geography**度数でインスタンス。  
  
 これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **float**  
  
 CLR の戻り値の型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 このメソッドが戻るポイント、 **geography**度数でインスタンス。 EnvelopeCenter() を使用すると`EnvelopeAngle()`の外接する円を返します、 **geography**インスタンス。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、このメソッドが拡張されて**FullGlobe**インスタンス。  
  
 適用された半球に関する制限`EnvelopeAngle()`で[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]は削除されました。 ただし、90 度を超える角度のインスタンスの場合、180 度が返されます。 `EnvelopeAngle()`正確ではない**geography**複数の半球にまたがるインスタンス。  
  
## <a name="examples"></a>使用例  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40;geography データ型&#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  
