---
title: "AsTextZM (geometry データ型) |Microsoft ドキュメント"
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
- AsTextZM_TSQL
- AsTextZM
- AsTextZM (geometry Data Type)
- AsTextZM_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM (geometry Data Type)
ms.assetid: 08ac8aa0-aff7-4b22-87e0-1a1d55dcbc04
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 91f77bd684d79bbef2530307aa65fc0d92b91c5e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="astextzm-geometry-data-type"></a>AsTextZM (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

いずれかで補完された geometry インスタンスの Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現を返します**Z** (標高) と**M** (メジャー) 値が、インスタンスで実行します。
  
## <a name="syntax"></a>構文  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **nvarchar (max)**  
  
 CLR の戻り値の型: **SqlChars**  
  
## <a name="remarks"></a>解説  
  
## <a name="examples"></a>使用例  
 次の例を作成、`Point`インスタンスを含む**Z** (標高) と**M** (メジャー) 値です。 `STAsText()`選択 WKT 値 (1 2) です。`AsTextZM()`同じ WKT 値を選択し、またの値を返します**Z**と**M**、(1 2 3 4) を生成します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [M (&) #40";"geometry データ型"&"#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [Z & #40";"geometry データ型"&"#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  


