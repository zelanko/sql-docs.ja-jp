---
title: "ConvexHullAggregate (geography データ型) | Microsoft Docs"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ConvexHullAggregate_TSQL
- ConvexHullAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- ConvexHullAggregate method (geography)
ms.assetid: 21784c66-2725-471b-9e2d-a8c2e3695197
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dfbddd12cab58c441925fa113226adb4b671af46
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="convexhullaggregate-geography-data-type"></a>ConvexHullAggregate (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

指定された一連の **geography** オブジェクトに対して凸包を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>引数  
 *geography_operand*  
 **geography** オブジェクトのセットを表す **geography** 型のテーブルの列です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
## <a name="exception"></a>例外  
 入力値が無効である場合は、`FormatException` をスローします。 「[STIsValid &#40;geography Data Type&#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 メソッドは、入力が空か、入力にさまざまな SRID が含まれているときに **null** を返します。 「[SRID (Spatial Reference Identifier)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)」を参照してください。  
  
 メソッドでは、**null** 入力は無視されます。  
  
> [!NOTE]  
>  メソッドは、入力された値がすべて **null**の場合、**null** を返します。  
  
## <a name="examples"></a>使用例  
 次の例は、**geography** オブジェクトのセットの凸包を返します。  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::ConvexHullAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>参照  
 [拡張された静的な地理メソッド](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
